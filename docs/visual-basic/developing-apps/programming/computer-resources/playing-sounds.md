---
title: "Ses Çalma [Visual Basic]"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be5cec634482bf99ddff4ff6b6af8e897c4909e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="6d2ea-102">Ses Çalma [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="6d2ea-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="6d2ea-103">`My.Computer.Audio` Nesne ses çalma için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="6d2ea-104">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="6d2ea-104">Playing Sounds</span></span>  
 <span data-ttu-id="6d2ea-105">Arka plan çalma sesi çalar sırada başka bir kod yürütmek uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="6d2ea-106">`My.Computer.Audio.Play` Yöntemi yalnızca bir arka plan aynı anda ses çalınmaya uygulama sağlar; uygulama yeni bir arka plan ses yürütüldüğünde, önceki arka plan ses çalma durdurur.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="6d2ea-107">Ses çalma ve tamamlanmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="6d2ea-108">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi ses çalar.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="6d2ea-109">Zaman `AudioPlayMode.WaitToComplete` belirtilirse, `My.Computer.Audio.Play` kodu çağırma devam etmeden önce ses tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="6d2ea-110">Bu örnek kullanırken, dosya adı bilgisayarınızda bulunan bir .wav ses dosyası başvurduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="6d2ea-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 <span data-ttu-id="6d2ea-111">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi ses çalar.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="6d2ea-112">Bu örnek kullanırken, uygulama kaynaklarını Waterfall adlı bir .wav ses dosyası eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="6d2ea-113">Döngü ses çalma</span><span class="sxs-lookup"><span data-stu-id="6d2ea-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="6d2ea-114">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi oynadığı belirtilen ses arka planda olduğunda `PlayMode.BackgroundLoop` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="6d2ea-115">Bu örnek kullanırken, dosya adı bilgisayarınızda bulunan bir .wav ses dosyası başvurduğu emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 <span data-ttu-id="6d2ea-116">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi oynadığı belirtilen ses arka planda olduğunda `PlayMode.BackgroundLoop` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="6d2ea-117">Bu örnek kullanırken, uygulama kaynaklarını Waterfall adlı bir .wav ses dosyası eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 <span data-ttu-id="6d2ea-118">Önceki kod örneğinde bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6d2ea-119">Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Ses**.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="6d2ea-120">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="6d2ea-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="6d2ea-121">Bir uygulama döngü ses yürütüldüğünde, genel olarak, bu sonunda ses durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="6d2ea-122">Arka planda ses çalma durdurma</span><span class="sxs-lookup"><span data-stu-id="6d2ea-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="6d2ea-123">Kullanım `My.Computer.Audio.Stop` yöntemi uygulamanın arka plan oynatılmakta veya sesi döngü durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="6d2ea-124">Genel olarak, bir uygulama döngü ses yürütüldüğünde, ses, belirli bir noktada durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="6d2ea-125">Aşağıdaki örnek, arka planda yürütülen ses durdurur.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 <span data-ttu-id="6d2ea-126">Önceki kod örneğinde bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6d2ea-127">Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Ses**.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="6d2ea-128">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="6d2ea-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="6d2ea-129">Sistem ses çalma</span><span class="sxs-lookup"><span data-stu-id="6d2ea-129">Playing System Sounds</span></span>  
 <span data-ttu-id="6d2ea-130">Kullanım `My.Computer.Audio.PlaySystemSound` belirtilen sistem ses çalınmaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="6d2ea-131">`My.Computer.Audio.PlaySystemSound` Yöntemi bir parametresinden paylaşılan üyelerinden biri olarak aldığı <xref:System.Media.SystemSound> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="6d2ea-132">Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="6d2ea-133">Aşağıdaki örnek kullanır `My.Computer.Audio.PlaySystemSound` bir sistem ses çalınmaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d2ea-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2ea-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Audio>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>  
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>  
 <xref:Microsoft.VisualBasic.AudioPlayMode>
