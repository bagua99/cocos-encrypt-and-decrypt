
local gaofang = class("gaofang")

function gaofang:ctor(...)
	local args = {...}
	self.succeedCall = args[1]
	self.failedCall = args[2]
end

function gaofang:request()
	secure.log("gaofang request")
	self:reset()
	
	self.ip = secure.gaofang.ip
	secure.log("gaofang response:" .. self.ip)
	if self.succeedCall then
		self.succeedCall(self)
	end
end

function gaofang:getIP()
	secure.log("gaofang getIP:" .. self.ip)
	return self.ip
end

function gaofang:getName()
	return "gaofang"
end

function gaofang:reset()
	self.ip = nil
end

return gaofang