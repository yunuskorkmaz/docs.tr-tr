---
title: Ses Çalma
ms.date: 07/20/2015
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
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345516"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="e5528-102">Ses Çalma [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="e5528-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="e5528-103">Nesnesi `My.Computer.Audio` , ses çalmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5528-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="e5528-104">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="e5528-104">Playing Sounds</span></span>  

 <span data-ttu-id="e5528-105">Arka planda yürütme, ses çalarken uygulamanın diğer kodu yürütmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5528-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="e5528-106">`My.Computer.Audio.Play` Yöntemi, uygulamanın her seferinde yalnızca bir arka plan sesi oynamasını sağlar; uygulama yeni bir arka plan sesi yürüttüğünde, önceki arka plan sesinin çalınmasını bırakır.</span><span class="sxs-lookup"><span data-stu-id="e5528-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="e5528-107">Ayrıca bir ses oynatabilir ve tamamlanmasını bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5528-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="e5528-108">Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar.</span><span class="sxs-lookup"><span data-stu-id="e5528-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="e5528-109">`AudioPlayMode.WaitToComplete` Belirtildiğinde, `My.Computer.Audio.Play` kod çağrılmadan önce ses tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="e5528-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="e5528-110">Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız</span><span class="sxs-lookup"><span data-stu-id="e5528-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="e5528-111">Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar.</span><span class="sxs-lookup"><span data-stu-id="e5528-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="e5528-112">Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5528-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="e5528-113">Döngü seslerini oynama</span><span class="sxs-lookup"><span data-stu-id="e5528-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="e5528-114">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda `PlayMode.BackgroundLoop` yürütür.</span><span class="sxs-lookup"><span data-stu-id="e5528-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="e5528-115">Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e5528-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="e5528-116">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda `PlayMode.BackgroundLoop` yürütür.</span><span class="sxs-lookup"><span data-stu-id="e5528-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="e5528-117">Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5528-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="e5528-118">Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5528-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e5528-119">Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses**bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5528-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="e5528-120">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e5528-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="e5528-121">Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, sonunda sesi durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5528-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="e5528-122">Arka planda seslerin çalınmasını durdurma</span><span class="sxs-lookup"><span data-stu-id="e5528-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="e5528-123">Uygulamanın şu `My.Computer.Audio.Stop` anda yürütülmekte olan arka plan veya döngü sesini durdurmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5528-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="e5528-124">Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, bir noktada sesi durdurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5528-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="e5528-125">Aşağıdaki örnek, arka planda oynatılan bir sesi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e5528-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="e5528-126">Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5528-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e5528-127">Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses**bulunur.</span><span class="sxs-lookup"><span data-stu-id="e5528-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="e5528-128">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e5528-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="e5528-129">Sistem seslerini oynama</span><span class="sxs-lookup"><span data-stu-id="e5528-129">Playing System Sounds</span></span>  

 <span data-ttu-id="e5528-130">Belirtilen sistem `My.Computer.Audio.PlaySystemSound` sesini çalmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5528-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="e5528-131">Yöntemi `My.Computer.Audio.PlaySystemSound` , <xref:System.Media.SystemSound> sınıfından paylaşılan üyelerden birini parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e5528-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="e5528-132">Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5528-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="e5528-133">Aşağıdaki örnek, bir sistem `My.Computer.Audio.PlaySystemSound` sesini çalmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5528-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="e5528-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5528-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
