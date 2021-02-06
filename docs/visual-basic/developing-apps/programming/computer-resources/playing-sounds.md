---
description: 'Daha fazla bilgi edinin: sesleri oynatma (Visual Basic)'
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
ms.openlocfilehash: 247af8274108ca8374cf87e53aa2aaad8e5e736c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641518"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="15b0b-103">Ses Çalma [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="15b0b-103">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="15b0b-104">`My.Computer.Audio`Nesnesi, ses çalmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="15b0b-104">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="15b0b-105">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="15b0b-105">Playing Sounds</span></span>  

 <span data-ttu-id="15b0b-106">Arka planda yürütme, ses çalarken uygulamanın diğer kodu yürütmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="15b0b-106">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="15b0b-107">Yöntemi, uygulamanın tek seferde `My.Computer.Audio.Play` yalnızca bir arka plan sesi oynamasına izin verir; uygulama yeni bir arka plan sesi oynadığında, önceki arka plan sesini çalmayı bırakır.</span><span class="sxs-lookup"><span data-stu-id="15b0b-107">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="15b0b-108">Ayrıca bir ses oynatabilir ve tamamlanmasını bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15b0b-108">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="15b0b-109">Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar.</span><span class="sxs-lookup"><span data-stu-id="15b0b-109">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="15b0b-110">`AudioPlayMode.WaitToComplete`Belirtildiğinde, `My.Computer.Audio.Play` kod çağrılmadan önce ses tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="15b0b-110">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="15b0b-111">Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız</span><span class="sxs-lookup"><span data-stu-id="15b0b-111">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="15b0b-112">Aşağıdaki örnekte `My.Computer.Audio.Play` Yöntem bir ses oynar.</span><span class="sxs-lookup"><span data-stu-id="15b0b-112">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="15b0b-113">Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-113">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="15b0b-114">Döngü seslerini oynama</span><span class="sxs-lookup"><span data-stu-id="15b0b-114">Playing Looping Sounds</span></span>  

 <span data-ttu-id="15b0b-115">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda yürütür `PlayMode.BackgroundLoop` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-115">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="15b0b-116">Bu örneği kullanırken, dosya adının bilgisayarınızdaki bir. wav ses dosyasına başvurduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="15b0b-116">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="15b0b-117">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi belirtildiğinde belirtilen sesi arka planda yürütür `PlayMode.BackgroundLoop` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-117">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="15b0b-118">Bu örneği kullanırken, uygulama kaynaklarının şelale adlı bir. wav ses dosyası içerdiğinden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-118">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="15b0b-119">Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-119">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="15b0b-120">Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses** bulunur.</span><span class="sxs-lookup"><span data-stu-id="15b0b-120">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="15b0b-121">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="15b0b-121">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="15b0b-122">Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, sonunda sesi durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-122">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="15b0b-123">Arka planda seslerin çalınmasını durdurma</span><span class="sxs-lookup"><span data-stu-id="15b0b-123">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="15b0b-124">`My.Computer.Audio.Stop`Uygulamanın Şu anda yürütülmekte olan arka plan veya döngü sesini durdurmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="15b0b-124">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="15b0b-125">Genel olarak, bir uygulama bir döngü sesi yürüttüğünde, bir noktada sesi durdurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15b0b-125">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="15b0b-126">Aşağıdaki örnek, arka planda oynatılan bir sesi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="15b0b-126">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="15b0b-127">Yukarıdaki kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-127">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="15b0b-128">Kod parçacığı seçicide, **Windows Forms uygulamalarda > ses** bulunur.</span><span class="sxs-lookup"><span data-stu-id="15b0b-128">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="15b0b-129">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="15b0b-129">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="15b0b-130">Sistem seslerini oynama</span><span class="sxs-lookup"><span data-stu-id="15b0b-130">Playing System Sounds</span></span>  

 <span data-ttu-id="15b0b-131">`My.Computer.Audio.PlaySystemSound`Belirtilen sistem sesini çalmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="15b0b-131">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="15b0b-132">`My.Computer.Audio.PlaySystemSound`Yöntemi, sınıfından paylaşılan üyelerden birini parametre olarak alır <xref:System.Media.SystemSound> .</span><span class="sxs-lookup"><span data-stu-id="15b0b-132">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="15b0b-133">Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="15b0b-133">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="15b0b-134">Aşağıdaki örnek, `My.Computer.Audio.PlaySystemSound` bir sistem sesini çalmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="15b0b-134">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="15b0b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15b0b-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
