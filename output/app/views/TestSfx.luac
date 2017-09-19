
local gt = cc.exports.gt

require("app/Sound")

local TestSfx = class("TestSfx", function()
	return cc.Scene:create()
end)

function TestSfx:ctor()
	local csbNode = cc.CSLoader:createNode("TestSfx.csb")
	csbNode:setAnchorPoint(0.5, 0.5)
	csbNode:setPosition(gt.winCenter)
	self:addChild(csbNode)

	self.sfxTable = {
		{
			fileName = "PVESkill_name_10010",
			level = 9
		},
		{
			fileName = "mortar",
			level = 2
		},
		{
			fileName = "mortar_fire_01",
			level = 2
		}
	}

	self.sfxAddCount = {0, 0, 0}

	for i = 1, 3 do
		local sfxBtn = gt.seekNodeByName(csbNode, "Btn_addSfx_" .. i)
		sfxBtn:setTag(i)
		gt.addBtnPressedListener(sfxBtn, function(sender)
			local sfxTag = sender:getTag()
			-- local sfxData = sfxTable[sfxTag]
			-- Sound.playEffect(sfxData.fileName, false, sfxData.level)
			self.sfxAddCount[sfxTag] = self.sfxAddCount[sfxTag] + 10
		end)
	end

	gt.scheduler:scheduleScriptFunc(handler(self, self.update), 0.25, false)
end

function TestSfx:update(delta)
	for i, sfxCount in ipairs(self.sfxAddCount) do
		if sfxCount > 0 then
			local sfxData = self.sfxTable[i]
			Sound.playEffect(sfxData.fileName, false, sfxData.level)

			self.sfxAddCount[i] = self.sfxAddCount[i] - 1
		end
	end
end

return TestSfx

