-- Creator ArthurSong
-- Create Time 2015/06/03

local gt = cc.exports.gt

require("app/localizations/ch_cn")

-- local LocalizationPackages =
-- {
	-- ["zh-CN"] = require("app/localizations/zh-CN"),
	-- ["eh-CN"] = require("app/localizations/en-CN")
-- }
-- local currentLanguage = "zh-CN"
-- gt.localizationPackage = require("app/localizations/" .. currentLanguage)

local function getLocationString(key, ...)
	if ("string" ~= type(key)) then
		return "nil";
	end

	local ltString = gt.LocationStrings[key] or gt.localizationPackage[key] or key;

	if( _G.next({...}) ) then
		ltString = string.format(ltString, ...)
	end

	return ltString
end
gt.getLocationString = getLocationString



