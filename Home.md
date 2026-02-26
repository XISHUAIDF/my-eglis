---
---
```dataviewjs
dv.span("### 📚 学习时长分布 (分钟)")

const calendarData = {
    year: 2026, // 你可以根据需要修改年份
    colors: {
        high: ["#1e6823", "#44a340", "#8cc665", "#c6e48b", "#ebedf0"], // 绿色系
    },
    entries: []
}

// 抓取包含 study_time 的日记
for (let page of dv.pages('"日记文件夹路径"').where(p => p.study_time)) {
    calendarData.entries.push({
        date: page.file.name, // 确保你的文件名是 YYYY-MM-DD 格式
        intensity: page.study_time,
        content: await dv.span(`[${page.study_time}min]`), // 鼠标悬停显示内容
    })
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
const calendarData = {
    year: 2026,
    colors: {
        green: ["#ebedf0", "#9be9a8", "#40c463", "#30a14e", "#216e39"],
        navy: ["#ffb6c1", "#bf90a0", "#7f6a80", "#3f445f", "#001f3f"],
        gold: ["#ffb6c1", "#ffbe90", "#ffc660", "#ffce30", "#ffd700"]
    },
    entries: [],
    showCurrentDayBorder: true, // (optional) defaults to true
	defaultEntryIntensity: 4,   // (optional) defaults to 4
	intensityScaleStart: 0,    // (optional) defaults to lowest value passed to entries.intensity
	intensityScaleEnd: 100,     // (optional) defaults to highest value passed to 
}



for (let page of dv.pages("").where(p => p.master_rate)) {
    // 直接使用文件名（假设格式是 YYYY-MM-DD）
    const fileName = page.file.name;
    
    calendarData.entries.push({
        date: fileName,
        intensity: page.master_rate,          
		color: "green"
    })
}

renderHeatmapCalendar(this.container, calendarData)
```