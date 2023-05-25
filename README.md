# QBUSTOESX การแปลงสคริปต์ QBUS เป็น ESX การอัปเดตแบบไม่หยุดยั้ง
# DISCORD : WWW.DISCORD.GG/MDTYAZILIM
# (ไทย): ғɪʟᴍ'ᴢ ᴄʀᴢ
--------------------------------------------------------------------------------------------------
พื้นฐาน QBUS และ พื้นฐาน ESX
```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- การรอครั้งที่สอง
	end
end)
```
สำหรับรุ่นใหม่ที่อยู่ด้านล่าง -- สำหรับรุ่นเก่าที่อยู่ด้านบน หากไม่ได้ผล ให้ลองทั้งสองอย่าง
```lua
local QBCore = exports['qb-core']:GetCoreObject()
```

# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX = nil

Citizen.CreateThread(function()
  while ESX == nil do
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Citizen.Wait(30)-- การรอครั้งที่สอง
  end
end)
```

--------------------------------------------------------------------------------------------------

ท่านสุภาพบุรุษ ส่วนนี้ถูกเพิ่มเข้ามา
ความหมาย:
ส่วนอินพุตของผู้เล่นจำเป็นเมื่อเข้าสู่เกม นั่นคือไฟล์เซิร์ฟเวอร์
เหตุการณ์นี้เกิดขึ้นเมื่อผู้เล่นเชื่อมต่อกับเซิร์ฟเวอร์
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```

--------------------------------------------------------------------------------------------------

ไฟล์เซิร์ฟเวอร์ ส่วนงานคือส่วนอาชีพ
```lua
RegisterNetEvent('QBCore:Client:OnJobUpdate')
AddEventHandler('QBCore:Client:OnJobUpdade', 
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```

--------------------------------------------------------------------------------------------------

คุณสามารถตรวจสอบได้ที่นี่
https://esx-framework.github.io/es_extended/common/events/onplayerdeath/#example-client-side-usage
```lua
RegisterNetEvent('QBCore:Client:OnPlayerUnload')
AddEventHandler('QBCore:Client:OnPlayerUnload',
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
RegisterNetEvent('esx:onPlayerDeath')
AddEventHandler('esx:onPlayerDeath',
```

--------------------------------------------------------------------------------------------------

ท่านสุภาพบุรุษ ส่วนนี้ถูกเพิ่มเข้ามา
ความหมาย:
ฟังก์ชันนี้จะรับ ไอดี ไคลเอ็นต์ของผู้เล่นที่ใกล้ที่สุดและระยะห่างไปยังผู้เล่น
```lua
QBCore.Functions.GetClosestPlayer()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetClosestPlayer()
```

--------------------------------------------------------------------------------------------------

การเพิ่มข้อความ 3 มิติ ไฟล์ไคลเอนต์ ตัวอย่าง : https://media.discordapp.net/attachments/623207764314816562/812096508786507806/image_1.png
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'ตัวอย่าง')
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
DrawText3D(1, 1, 1, 'ตัวอย่าง') -- (คุณต้องเปิดฟังก์ชันด้านล่าง)
ESX.Game.Utils.DrawText3D(1, 1, 1, 'ตัวอย่าง') -- ESX ไม่จำเป็นต้องใช้ ฟังก์ชันนี้มีอยู่แล้ว
```

--------------------------------------------------------------------------------------------------

เมนู เปิด/ปิด เมนูในตัวอย่าง ESX & QBCore: https://prnt.sc/u4f7s5
```lua
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (คุณต้องติดตั้งสคริปต์เริ่มต้นของเมนู)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```

--------------------------------------------------------------------------------------------------

ตัวอย่างสคริปต์การแจ้งเตือน: https://dosya.turkmmo.com/2020/09/36521_efa54848705a4069cbedfc2770e50cf1.png
```lua
TriggerClientEvent("QBCore:Notify", "ข้อความ.", "success", 2500)

-- เซิร์ฟเวอร์บน -- ไคลเอนต์ล่าง

QBCore.Functions.Notify("ข้อความ.", "error")
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
TriggerEvent('Notification',"ข้อความ.")

-- เซิร์ฟเวอร์บน -- ไคลเอนต์ล่าง

ESX.ShowHelpNotification('ข้อความ.')
```

--------------------------------------------------------------------------------------------------

ส่วนไอเทมช่องเก็บของ
```lua
xPlayer.Functions.GetItemByName 
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.getInventoryItem
```
--------------------------------------------------------------------------------------------------

```lua
xPlayer.PlayerData.name 
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.getName()
```

--------------------------------------------------------------------------------------------------

รหัสเริ่มงาน
```lua
RegisterNetEvent('QBCore:Client:OnJobUpdate')
AddEventHandler('QBCore:Client:OnJobUpdate', function(job)
    PlayerData.job = job
end)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob', function(job)
    PlayerData.job = job
end)
```

--------------------------------------------------------------------------------------------------

ให้เงินรับเงินส่วน
```lua
Player.Functions.AddMoney('bank', amount, "ฝากเงินธนาคาร") -- เพิ่มเงิน
Player.Functions.RemoveMoney('cash', amount, "ฝากเงินธนาคาร") -- ลบเงิน
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.removeAccountMoney('bank', amount) -- ลบเงิน
xPlayer.addMoney(amount) -- เพิ่มเงิน
```

--------------------------------------------------------------------------------------------------

ข้อมูลส่วนเงิน
```lua
Player.PlayerData.money["bank"]
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.getAccount('bank').money
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.IsSpawnPointClear()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.IsSpawnPointClear()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.SetVehicleProperties()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.SetVehicleProperties()
```

--------------------------------------------------------------------------------------------------

ส่วนการลบไอเทมช่องเก็บของ
```lua
xPlayer.Functions.RemoveItem 
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.removeInventoryItem 
```

--------------------------------------------------------------------------------------------------

การเพิ่มไอเทมช่องเก็บของ
```lua
xPlayer.Functions.AddItem
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.addInventoryItem
```

--------------------------------------------------------------------------------------------------

ส่วนตัวละครเป็นเหมือนรหัสของผู้เล่น
```lua
QBCore.Functions.GetPlayer(src)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.GetPlayerFromId(src)
```

--------------------------------------------------------------------------------------------------

ดึงผู้เล่นทุกคน
```lua
QBCore.Functions.GetPlayers(src)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.GetPlayers(src)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPlayerByCitizenId(src)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.GetPlayerFromIdentifier(src)
```

--------------------------------------------------------------------------------------------------

ฟังก์ชันนี้ตัดแต่งข้อความ ลบช่องว่างด้านหลังทั้งหมด โดยปกติแล้ว `GetVehicleNumberPlateText()` จะใช้เมื่อทำการฆ่าเชื้อในพื้นที่
#ตัวอย่าง
```lua
QBCore.Functions.MathTrim(GetVehicleNumberPlateText(vehicle))
````
#standart
```lua
QBCore.Functions.MathTrim 
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Math.Trim(value)
```

--------------------------------------------------------------------------------------------------

ไม่เป็นที่รู้จักในเรื่องนี้จะได้รับการอัปเดต
#ตัวอย่าง
```lua
QBCore.Functions.MathRound(GetVehicleBodyHealth(vehicle), 1),
```
#มาตรฐาน
```lua
QBCore.Functions.MathRound()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
# ตัวอย่าง
```lua
local deger - 5.444

print ('value:' .. value) - 5.444 -- ผลตอบแทน
print ('value rounded up:' .. ESX.Math.Round(value)) -- 5 ผลตอบแทน
print ('value rounded up:' .. ESX.Math.Round(value, 1)) -- 5, 4 ผลตอบแทน
```
#มาตรฐาน
```lua
ESX.Math.Round(value, numberDecimals)
```

--------------------------------------------------------------------------------------------------

ตำแหน่งวางไข่ของรถยนต์
```lua
QBCore.Functions.SpawnVehicle()
QBCore.Functions.DeleteVehicle()
QBCore.Functions.GetVehicleProperties()
QBCore.Functions.GetClosestVehicle()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.SpawnVehicle()
ESX.Game.DeleteVehicle()
ESX.Game.GetVehicleProperties()
ESX.Game.GetClosestVehicle()
```
--(ถ้า ESX.Game เกือบทุกอย่างจะเหมือนกับ QBCore.Functions)


--------------------------------------------------------------------------------------------------

**สำหรับรถที่จะดึงป้ายทะเบียน กล่าวคือ ถ้าป้ายของรถตัวอย่างเป็นแบบ [ 01MDT34 ] ก็จะดึงป้ายนี้โดยตรง**
**ตำแหน่งที่จะใช้รหัสคือ QBCore: `qb-core/client/functions.lua`**

```lua
function QBCore.Functions.GetPlate(vehicle)
    if vehicle == 0 then return end
    return QBCore.Shared.Trim(GetVehicleNumberPlateText(vehicle))
end
```
# ด้านบน QBUSCORE

**ตำแหน่งที่จะใช้รหัสคือ ESX: `es_extended/client/functions.lua`**
# ด้านล่าง ESX
```lua
function ESX.GetPlate(vehicle)
    if vehicle == 0 then return end
    return ESX.Math.Trim(GetVehicleNumberPlateText(vehicle))
end
```

--------------------------------------------------------------------------------------------------

**ขอดูรุ่นรถ**
**ตำแหน่งที่จะใช้รหัสคือ QBCore: `qb-core/client/functions.lua`**

```lua
function QBCore.Functions.GetVehicleLabel(vehicle)
    if vehicle == nil or vehicle == 0 then return end
    return GetLabelText(GetDisplayNameFromVehicleModel(GetEntityModel(vehicle)))
end
```
# ด้านบน QBUSCORE

**ตำแหน่งที่จะใช้รหัสคือ ESX: `es_extended/client/functions.lua: ไปที่ด้านล่างกันเถอะ`**
# ด้านล่าง ESX
```lua
function ESX.GetVehicleLabel(vehicle)
    if vehicle == nil or vehicle == 0 then return end
    return GetLabelText(GetDisplayNameFromVehicleModel(GetEntityModel(vehicle)))
end
```

--------------------------------------------------------------------------------------------------


วางรหัสเหล่านี้ที่นี่: วาง `qb-core/client/functions.lua:160`
ตำแหน่งวางไข่ของรถยนต์
```lua
QBCore.Functions.GetVehiclesInArea = function(coords, maxDistance) return EnumerateEntitiesWithinDistance(QBCore.Functions.GetVehicles(), false, coords, maxDistance) end
QBCore.Functions.IsSpawnPointClear = function(coords, maxDistance) return #QBCore.Functions.GetVehiclesInArea(coords, maxDistance) == 0 end
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetVehiclesInArea = function(coords, maxDistance) return EnumerateEntitiesWithinDistance(ESX.Game.GetVehicles(), false, coords, maxDistance) end
ESX.Game.IsSpawnPointClear = function(coords, maxDistance) return #ESX.Game.GetVehiclesInArea(coords, maxDistance) == 0 end
```
--(เกือบทุกอย่างที่เป็น ESX.Game จะเหมือนกับ QBCore.Functions)

--------------------------------------------------------------------------------------------------

`qb-core/client/functions.lua`
ทำสิ่งนี้ในไคลเอนต์ qb-core functions.lua วางไว้ในบรรทัดว่าง
```lua
function QBCore.Functions.RequestNamedPtfxAsset(assetName, cb)
	if not HasNamedPtfxAssetLoaded(assetName) then
		RequestNamedPtfxAsset(assetName)

		while not HasNamedPtfxAssetLoaded(assetName) do
			Citizen.Wait(1)
		end
	end

	if cb ~= nil then
		cb()
	end
end
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
function ESX.Streaming.RequestNamedPtfxAsset(assetName, cb)
	if not HasNamedPtfxAssetLoaded(assetName) then
		RequestNamedPtfxAsset(assetName)

		while not HasNamedPtfxAssetLoaded(assetName) do
			Citizen.Wait(1)
		end
	end

	if cb ~= nil then
		cb()
	end
end
```


--------------------------------------------------------------------------------------------------

`qb-core/client/functions.lua`
ทำสิ่งนี้ในไคลเอนต์ qb-core functions.lua วางไว้ในบรรทัดว่าง
```lua
function QBCore.Functions.DeleteObject(object)
	SetEntityAsMissionEntity(object, false, true)
	DeleteObject(object)
end
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
function ESX.Game.DeleteObject(object)
	SetEntityAsMissionEntity(object, false, true)
	DeleteObject(object)
end
```

--------------------------------------------------------------------------------------------------

`qb-core/server/functions.lua`
ทำสิ่งนี้ในเซิร์ฟเวอร์ qb-core functions.lua วางไว้ในบรรทัดว่าง
```lua
function QBCore.Functions.GetItemLabel(item)
	if QBCore.UseableItems[item] ~= nil then
		return QBCore.UseableItems[item].label
	end
end
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
function ESX.GetItemLabel(item)
	if ESX.Items[item] then
		return ESX.Items[item].label
	end
end
```

--------------------------------------------------------------------------------------------------

ตัวละครของคุณเอง
```lua
QBCore.Functions.GetPlayerData()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.GetPlayerData()
```

--------------------------------------------------------------------------------------------------

การสร้างไอเทม
```lua
QBCore.Functions.CreateUseableItem()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.RegisterUsableItem()
```

--------------------------------------------------------------------------------------------------

การถอนเงินธนาคาร
```lua
Player.Functions.RemoveMoney()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
xPlayer.removeMoney(money)
```

--------------------------------------------------------------------------------------------------

เกี่ยวกับไฟล์
```lua
QBCore.Functions.CreateCallback()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.RegisterServerCallback()
```

--------------------------------------------------------------------------------------------------

เกี่ยวกับไฟล์
```lua
QBCore.Functions.TriggerCallback()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.TriggerServerCallback()
```

--------------------------------------------------------------------------------------------------

IDENTIFIER IS USED IN CID ESX IN QB I LEFT A SMALL CODE BLOCK FOR YOU TO SOLVE THE EVENT
```lua
QBCore.Functions.CreateCallback('system:fetchStatus', function(source, cb)
    local Player = QBCore.Functions.GetPlayer(source)

     if Player then
           exports['ghmattimysql']:execute('SELECT skills FROM players WHERE citizenid = @citizenid', {
               ['@citizenid'] = Player.PlayerData.citizenid
          }, function(status)
              if status ~= nil then
                   cb(json.decode(status))
              else
                   cb(nil)
              end
          end)
     else
          cb()
     end
end)
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.RegisterServerCallback("system:fetchStatus", function(source, cb)
    local src = source
    local user = ESX.GetPlayerFromId(src)


    local fetch = [[
          SELECT
               skills
          FROM
               users
          WHERE
               identifier = @identifier
    ]]

     MySQL.Async.fetchScalar(fetch, {
          ["@identifier"] = user.identifier

     }, function(status)

          if status ~= nil then
               cb(json.decode(status))
          else
               cb(nil)
          end

     end)
end)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Items
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.GetItems()
```
--------------------------------------------------------------------------------------------------

ส่วนของการเชื่อมโยง SQL
```lua
QBCore.Functions.ExecuteSql()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```

--------------------------------------------------------------------------------------------------


RegisterCommand - ส่วนคำสั่งแชท
```lua
QBCore.Commands.Add()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
RegisterCommand 
```
-- (REGISTERCOMMAND ทำงานใน QBCORE ได้ด้วย)

--------------------------------------------------------------------------------------------------

การผูกส่วนอักขระข้อมูลผบ.
```lua
local Player = QBCore.Functions.GetPlayer(source)
['@citizenid'] = Player.PlayerData.citizenid -- ดึงผู้เล่น
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
local user = ESX.GetPlayerFromId(src)
["@identifier"] = user.identifier -- ดึงผู้ใช้
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Trim()
QBCore.Shared.GroupDigits()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Math.Trim()
ESX.Math.GroupDigits()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestObject()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetClosestObject()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetVehicleInDirection()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetVehicleInDirection()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPeds()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetPeds()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetObjects()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetObjects()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestPed()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.GetClosestPed()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.SpawnObject()
```
# ด้านบน QBUSCORE

# ด้านล่าง ESX
```lua
ESX.Game.SpawnObject()
```

------------------------------------------------------------------------------------------------
