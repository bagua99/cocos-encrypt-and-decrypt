
local gt = cc.exports.gt

local Sound = class("Sound")

function Sound:ctor()
	ccexp.AudioEngine:lazyInit()

	local soundEftPercent = cc.UserDefault:getInstance():getIntegerForKey("Sound_Eft_Percent", 100)
	self.soundEffectVolume = soundEftPercent

	local musicPercent = cc.UserDefault:getInstance():getIntegerForKey("Music_Percent", 100)
	self.musicVolume = musicPercent

	gt.log(string.format("soundEffectVolume:[%f] musicVolume:[%f]", self.soundEffectVolume, self.musicVolume))
end

-- start --
--------------------------------
-- @class function
-- @description 恢复声音播放
-- end --
function Sound:resumeAllSound()
	ccexp.AudioEngine:resumeAll()
end

-- start --
--------------------------------
-- @class function
-- @description 暂停声音播放
-- end --
function Sound:pauseAllSound()
	ccexp.AudioEngine:pauseAll()
end

-- start --
--------------------------------
-- @class function
-- @description 设置特效音量
-- @param 音量值0~1
-- end --
function Sound:setSoundEffectVolume(soundEffectVolume)
	self.soundEffectVolume = soundEffectVolume

	cc.UserDefault:getInstance():setIntegerForKey("Sound_Eft_Percent", soundEffectVolume)
end

function Sound:getSoundEffectVolume()
	return self.soundEffectVolume
end

-- start --
--------------------------------
-- @class function
-- @description 播放后背景音乐
-- @param musicVolume 音乐音量
-- end --
function Sound:setMusicVolume(musicVolume)
	self.musicVolume = musicVolume

	if self.musicAudioID then
		ccexp.AudioEngine:setVolume(self.musicAudioID, musicVolume * 0.01)
	end

	cc.UserDefault:getInstance():setIntegerForKey("Music_Percent", musicVolume)
end

function Sound:getMusicVolume()
	return self.musicVolume
end

-- start --
--------------------------------
-- @class function
-- @description 播放音效
-- @param fileName 音效名称
-- @param isLoop 是否循环
-- @return 音效id
-- end --
function Sound:playEffect(fileName, isLoop)
	-- 关闭声音并且非循环
	if not fileName or string.len(fileName) == 0 then
		return
	end

	local fileSuffix = "mp3"
	if device.platform == "android" then
		-- fileSuffix = "ogg"
	elseif device.platform == "ios" then
		-- fileSuffix = "caf"
	end
	local filePath = string.format("sfx/%s.%s", fileName, fileSuffix)
	isLoop = isLoop or false
	local audioID = ccexp.AudioEngine:play2d(filePath, isLoop, self.soundEffectVolume * 0.01)

	return audioID
end

-- start --
--------------------------------
-- @class function
-- @description 停止audioID音效
-- end --
function Sound:stopEffect(audioID)
	if not audioID then
		return
	end

	ccexp.AudioEngine:stop(audioID)
end

function Sound:playVoice(filePath)
	ccexp.AudioEngine:play2d(filePath)
end

-- start --
--------------------------------
-- @class function
-- @description 暂停音效
-- end --
function Sound:pauseEffect(audioID)
	if not audioID then
		return
	end

	ccexp.AudioEngine:pause(audioID)
end

-- start --
--------------------------------
-- @class function
-- @description 恢复音效
-- end --
function Sound:resumeEffect(audioID)
	if not audioID then
		return
	end

	ccexp.AudioEngine:resume(audioID)
end

-- start --
--------------------------------
-- @class function
-- @description 播放背景音
-- @param fileName 音效名称
-- @param isLoop 是否循环
-- end --
function Sound:playMusic(fileName, isLoop)
	if not fileName or string.len(fileName) == 0 then
		return
	end
	isLoop = isLoop or false
	self:stopMusic()
	self.musicAudioID = ccexp.AudioEngine:play2d(string.format("sfx/%s.mp3", fileName), isLoop, self.musicVolume * 0.01)
end

-- start --
--------------------------------
-- @class function
-- @description 停止播放背景声音
-- end --
function Sound:stopMusic()
	if not self.musicAudioID then
		return
	end

	ccexp.AudioEngine:stop(self.musicAudioID)
	self.musicAudioID = nil
end

return Sound



