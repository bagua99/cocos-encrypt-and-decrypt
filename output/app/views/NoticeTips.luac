
local gt = cc.exports.gt

local NoticeTips = class("NoticeTips", function()
	return gt.createMaskLayer()
end)

function NoticeTips:ctor(titleText, tipsText, okFunc, cancelFunc, singleBtn)
	self:setName("NoticeTips")

	local csbNode = cc.CSLoader:createNode("NoticeTips.csb")
	csbNode:setPosition(gt.winCenter)
	self:addChild(csbNode)

	if titleText then
		local titleLabel = gt.seekNodeByName(csbNode, "Label_title")
		titleLabel:setString(titleText)
	end

	if tipsText then
		local tipsLabel = gt.seekNodeByName(csbNode, "Label_tips")
		tipsLabel:setString(tipsText)
	end

	local okBtn = gt.seekNodeByName(csbNode, "Btn_ok")
	gt.addBtnPressedListener(okBtn, function()
		self:removeFromParent()
		if okFunc then
			okFunc()
		end
	end)

	local cancelBtn = gt.seekNodeByName(csbNode, "Btn_cancel")
	gt.addBtnPressedListener(cancelBtn, function()
		self:removeFromParent()
		if cancelFunc then
			cancelFunc()
		end
	end)

	if singleBtn then
		okBtn:setPositionX(0)
		cancelBtn:setVisible(false)
	end

	local runningScene = cc.Director:getInstance():getRunningScene()
	if runningScene then
		runningScene:addChild(self, gt.CommonZOrder.NOTICE_TIPS)
	end
end

return NoticeTips

