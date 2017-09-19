
local gt = cc.exports.gt

local LoadingTips = class("LoadingTips", function()
	return gt.createMaskLayer()
end)

function LoadingTips:ctor(tipsText)
	self:setName("LoadingTips")

	local tipsNode, tipsAnimation = gt.createCSAnimation("LoadingTips.csb")
	tipsAnimation:play("run", true)
	tipsNode:setPosition(gt.winCenter)
	self:addChild(tipsNode)

	local runningScene = cc.Director:getInstance():getRunningScene()
	if runningScene then
		runningScene:addChild(self, gt.CommonZOrder.LOADING_TIPS)
	end

	self:setTipsText(tipsText)
end

function LoadingTips:setTipsText(tipsText)
	if tipsText then
		local tipsLabel = gt.seekNodeByName(self, "Label_tips")
		tipsLabel:setString(tipsText)
	end
end

function LoadingTips:remove()
	self:removeFromParent()
end

return LoadingTips
