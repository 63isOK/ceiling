2020/11/20 周五

	- 目标: 用webrtc来接收音频,并传给dll,和trtc sdk结合
	- step1: 用webrtc来接收音频,播放(完成)
	- step2: 用webrtc来接收音频,播放+保存
	- step3: 用webrtc来接收音频,播放+传输,传输后保存(完成)
	- step4: 用webrtc来接收音频,播放+传输,传输将opus转为pcm,并保存(完成)
	- step5: 用webrtc来接收音频,播放+传输,传输将opus转为pcm,并传输给dll

	todo:
		- 抽取出aec算法,单独作为音频的处理模块,添加到dll中.

		opus的采样频率是48000,每次采样数为960,帧率是50,每次采样的时长是1/50 = 0.02秒.
		32位采样:
		2 x 960/48000 * 48000 * 4byte = 960*8byte

2020/11/25 周三

	aec用vad来检测人声,并用于处理啸叫问题.

	- 将48000/f32/双声道,改为16000/s16/单声道(完成)
	- 集成vad检测算法,查看检测结果.(完成)
	
	todo:
	- vad可链接版本
	- 确定vad其他项目每次采样的时长
	- 数据是怎么喂给Process的,是缓冲之后给,还是实时给
	
2020/11/26 周四

	集成webrtc的vad检测,最后发现vad只做静音和非静音,无法区分啸叫和人声
	
	- 查看腾讯那边对vad的做法