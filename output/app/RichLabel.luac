-- Creator ArthurSong
-- Create Time 2015/10/16

local RichLabel = class("RichLabel", function()
	return ccui.RichText:create()
end)

-- start --
--------------------------------
-- @class function
-- @description
-- @param contentText 文本内容(0,255,0|文本|0,255,0|文本)
-- @param fontSize 字体大小
-- @param contentSize 内容区域(如果为空不换行)
-- @param verticalSpace 行间距
-- end --
function RichLabel:ctor(contentText, fontSize, contentSize, verticalSpace)
	if not contentText then
		return
	end

	fontSize = fontSize or 18

	-- 内容显示区域
	if contentSize then
		self:ignoreContentAdaptWithSize(false)
		self:setContentSize(contentSize)
	else
		self:ignoreContentAdaptWithSize(true)
	end

	if verticalSpace then
		-- 行间距
		self:setVerticalSpace(verticalSpace)
	end

	self.textLen = 0
	local unitsArray = string.split(contentText, "|")
	local eleTag = 1
	for i = 1, #unitsArray, 2 do
		-- color
		local textColor = string.split(unitsArray[i], ",")
		-- text unitsArray[i + 1]
		local eleText = ccui.RichElementText:create(eleTag, cc.c3b(textColor[1], textColor[2], textColor[3]), 255, unitsArray[i + 1], gt.fontNormal, fontSize)
		self:pushBackElement(eleText)

		self.textLen = self.textLen + self:utfStrLen(unitsArray[i + 1])

		eleTag = eleTag + 1
	end
end

function RichLabel:getTextLen()
	return self.textLen
end

--- 获取utf8编码字符串正确长度的方法
-- @param str
-- @return number
function RichLabel:utfStrLen(str)
	local len = #str
	local left = len
	local cnt = 0
	local arr = {0, 0xc0, 0xe0, 0xf0, 0xf8, 0xfc}
	while left ~= 0 do
		local tmp = string.byte(str, -left)
		local i = #arr
		while arr[i] do
			if tmp >= arr[i] then
				left = left - i
				break
			end
			i = i - 1
		end
		cnt = cnt + 1
	end
	return cnt
end

return RichLabel
