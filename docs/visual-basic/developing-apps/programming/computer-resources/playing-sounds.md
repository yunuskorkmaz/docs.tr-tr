---
title: Ses Çalma [Visual Basic]
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
ms.openlocfilehash: 56b156545fac2aba09d32139fdaad26da711e018
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966222"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="502a3-102">Ses Çalma [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="502a3-102">Playing Sounds (Visual Basic)</span></span>
<span data-ttu-id="502a3-103">`My.Computer.Audio` Nesne sesleri çalmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="502a3-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="502a3-104">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="502a3-104">Playing Sounds</span></span>  
 <span data-ttu-id="502a3-105">Arka planda yürütmeyi uygulamanın ses çalar sırasında diğer kod yürütmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="502a3-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="502a3-106">`My.Computer.Audio.Play` Yöntemi uygulamanın aynı anda yalnızca bir arka plan sesli sağlar; uygulamanın yeni bir arka plan ses yürütüldüğünde, önceki arka plan ses yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="502a3-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="502a3-107">Ayrıca, bir ses çal ve tamamlanmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="502a3-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="502a3-108">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="502a3-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="502a3-109">Zaman `AudioPlayMode.WaitToComplete` belirtilen `My.Computer.Audio.Play` kodu çağırma devam etmeden önce sesi tamamlanana kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="502a3-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="502a3-110">Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyası başvurduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="502a3-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="502a3-111">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="502a3-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="502a3-112">Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="502a3-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="502a3-113">Döngü ses çalma</span><span class="sxs-lookup"><span data-stu-id="502a3-113">Playing Looping Sounds</span></span>  
 <span data-ttu-id="502a3-114">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="502a3-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="502a3-115">Bu örnek kullanırken, dosya adı bilgisayarınızda .wav ses dosyasına başvuruyor emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="502a3-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="502a3-116">Aşağıdaki örnekte, `My.Computer.Audio.Play` yöntemi arka planda belirtilen ses çalar olduğunda `PlayMode.BackgroundLoop` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="502a3-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="502a3-117">Bu örnek kullanırken, uygulama kaynaklarının Şelale adlı .wav ses dosyası eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="502a3-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="502a3-118">Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="502a3-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="502a3-119">Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**.</span><span class="sxs-lookup"><span data-stu-id="502a3-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="502a3-120">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="502a3-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="502a3-121">Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, ses sonunda durdurmak.</span><span class="sxs-lookup"><span data-stu-id="502a3-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="502a3-122">Ses arka planda yürütmeyi durdurma</span><span class="sxs-lookup"><span data-stu-id="502a3-122">Stopping the Playing of Sounds in the Background</span></span>  
 <span data-ttu-id="502a3-123">Kullanım `My.Computer.Audio.Stop` uygulamanın şu anda arka plan yürütme ya da ses döngü durdurmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="502a3-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="502a3-124">Genel olarak, bir uygulama dönen bir ses yürütüldüğünde, belirli bir noktada sesi durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="502a3-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="502a3-125">Aşağıdaki örnek, arkaplanda çalan bir sesi durdurur.</span><span class="sxs-lookup"><span data-stu-id="502a3-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="502a3-126">Yukarıdaki kod örneğinde, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="502a3-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="502a3-127">Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Ses**.</span><span class="sxs-lookup"><span data-stu-id="502a3-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="502a3-128">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="502a3-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="502a3-129">Sistem ses çalma</span><span class="sxs-lookup"><span data-stu-id="502a3-129">Playing System Sounds</span></span>  
 <span data-ttu-id="502a3-130">Kullanım `My.Computer.Audio.PlaySystemSound` sisteme ses çal için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="502a3-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="502a3-131">`My.Computer.Audio.PlaySystemSound` Yöntemi alır bir parametre olarak paylaşılan üyelerinden <xref:System.Media.SystemSound> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="502a3-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="502a3-132">Sistem sesi <xref:System.Media.SystemSounds.Asterisk%2A> genellikle hataları gösterir.</span><span class="sxs-lookup"><span data-stu-id="502a3-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="502a3-133">Aşağıdaki örnekte `My.Computer.Audio.PlaySystemSound` bir sistem ses çal için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="502a3-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="502a3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="502a3-134">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
