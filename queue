--[[
    author:zhouqili
    time:2019-05-07 10:51:03
]]

CircularQueue = {

}

function CircularQueue:new(nSize, szName)
    local q = {
        name = szName or "", 
        size = nSize,
        count = 0,
        head = 1,
        tail = 1,
        queue = {}
    }
    setmetatable(q, self)
    self.__index = self
    return q
end

function CircularQueue:empty()
    return self.count == 0
end

--[[
    @desc:          获取数据, 不出队列
    --@nOffset:     偏移量
    @return:        value or nil
]]
function CircularQueue:get(nOffset)
    if self:len() <= (nOffset or 0) then 
        return 
    end
    nOffset = nOffset and self.head + nOffset or self.head
    if nOffset > self.size then
        nOffset = nOffset - self.size
    end
    return self.queue[nOffset]
end

function CircularQueue:set(nIndex, value)
    self.queue[nIndex] = value
end

function CircularQueue:pop()
    if self:empty() then
        return false
    end
    local value = self.queue[self.head]
    if self.head == self.size then
        self.head = 1
    else
        self.head = self.head + 1
    end
    self.count = self.count - 1
    return value
end

function CircularQueue:push(value)
    if self:full() then
        return false
    end
    local pos = self.tail
    self.queue[self.tail] = value
    self.count = self.count + 1
    if self.tail == self.size then
        self.tail = 1
    else
        self.tail = self.tail + 1
    end
    return pos
end

function CircularQueue:len()
    return self.count
end

function CircularQueue:full()
    return self:len() >= self.size
end

function CircularQueue:print()
    print("CircularQueue:print", self.name, self.size, self.head, self.tail)
    if self:empty() then
        print("CircularQueue:print", 0)
        return 
    end
    if self.head >= self.tail then
        for i = self.head, self.size do
            print("CircularQueue:print", self.name, self.queue[i])
        end
        for i = 1, self.tail-1 do
            print("CircularQueue:print", self.name, self.queue[i])
        end
    else
        for i = self.head, self.tail-1 do
            print("CircularQueue:print", self.name, self.queue[i])
        end
    end
end

-- 获取距离队列头的间隔
function CircularQueue:getIntervals(nIndex)
    if nIndex < self.head then
        return self.size - self.head + nIndex + 1
    end
    return nIndex - self.head + 1
end
