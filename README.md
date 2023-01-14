# How-to-change-phone-number
This is a read me file so you know how to change your phone number and your account number

This is only for qbcore, fivem framework not real world xD <3 
Just a litle warning, these examples are for portugal, i used portuguese phone number and portuguese account number so if you are portuguese, Considera-te com sorte que tens aqui a papa toda feita xD. 

So, go on this path
qb-core/server/players.lua


# Phone number

Go on line 641 or search for the function called QBCore.functions.CreatePhoneNumber()

at the line 645 you can see that the variable is choosing random numbers, just change that as your like or you can do like this : 

  function QBCore.Functions.CreatePhoneNumber()
    local UniqueFound = false
    local PhoneNumber = nil
    while not UniqueFound do
        numero91 = 91
        numero92 = 92
        numero93 = 93
        numero96 = 96
        indicativo = math.random(0, 100)
        indicativo1 = nil
        if indicativo <= 25 then 
            indicativo1 = numero91
        elseif indicativo > 25 and indicativo <= 50 then
            indicativo1 = numero92
        elseif indicativo > 50 and indicativo <= 75 then
            indicativo1 = numero93
        else
            indicativo1 = numero96
        end
        PhoneNumber = indicativo1 .. math.random(1000000,9999999)
        local query = '%' .. PhoneNumber .. '%'
        local result = MySQL.prepare.await('SELECT COUNT(*) as count FROM players WHERE charinfo LIKE ?', { query })
        if result == 0 then
            UniqueFound = true
        end
    end
    return PhoneNumber
  end
  
  
  
  # Account number
  
  Go on line 627 or search for the function called QBCore.Functions.CreateAccountNumber()
  
  at line 631 you can see that the variable is choosing random numbers, just change that as your like or you can do like this :

function QBCore.Functions.CreateAccountNumber()
    local UniqueFound = false
    local AccountNumber = nil
    while not UniqueFound do
        AccountNumber = 'PT50' .. ' ' .. '00' .. math.random(10,99) .. ' ' .. math.random(0000, 9999) .. ' ' .. math.random(0000, 9999) .. ' ' .. math.random(0000, 9999) .. ' ' .. math.random(0000, 9999) .. ' ' .. math.random(0, 9)
        local query = '%' .. AccountNumber .. '%'
        local result = MySQL.prepare.await('SELECT COUNT(*) as count FROM players WHERE charinfo LIKE ?', { query })
        if result == 0 then
            UniqueFound = true
        end
    end
    return AccountNumber
end

any doubts go on discord and you can open a ticket or send me dm 
 # mt scripts 
 https://discord.gg/6kKKaAQ7cY

# My Discord
FlenN#9286
