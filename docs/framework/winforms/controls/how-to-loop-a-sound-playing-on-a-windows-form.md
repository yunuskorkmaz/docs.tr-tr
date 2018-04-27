---
title: 'Nasıl yapılır: Bir Windows Formda Sesi Döngü Olarak Çalma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6b4e910f30a5d125fd1ec234e896828738f62c4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="57f58-102">Nasıl yapılır: Bir Windows Formda Sesi Döngü Olarak Çalma</span><span class="sxs-lookup"><span data-stu-id="57f58-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="57f58-103">Aşağıdaki kod örneğinde ses sürekli olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="57f58-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="57f58-104">Olduğunda kodda `stopPlayingButton_Click` olay işleyicisi çalışır, durakları oynatılmakta ses.</span><span class="sxs-lookup"><span data-stu-id="57f58-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="57f58-105">Ses çalma, hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="57f58-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57f58-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="57f58-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57f58-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="57f58-107">Compiling the Code</span></span>  
 <span data-ttu-id="57f58-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="57f58-108">This example requires:</span></span>  
  
-   <span data-ttu-id="57f58-109">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="57f58-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="57f58-110">Dosya adı yerine `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adı ile.</span><span class="sxs-lookup"><span data-stu-id="57f58-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="57f58-111">Bu örnek visual Basic veya Visual C# için komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="57f58-111">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="57f58-112">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="57f58-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="57f58-113">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="57f58-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57f58-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="57f58-114">Robust Programming</span></span>  
 <span data-ttu-id="57f58-115">Dosya işlemleri içinde uygun özel durum işleme blok içine alınması.</span><span class="sxs-lookup"><span data-stu-id="57f58-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="57f58-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="57f58-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="57f58-117">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="57f58-117">The path name is malformed.</span></span> <span data-ttu-id="57f58-118">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk olan (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="57f58-119">Yolun salt okunurdur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="57f58-120">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="57f58-121">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="57f58-122">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="57f58-123">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="57f58-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="57f58-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="57f58-124">.NET Framework Security</span></span>  
 <span data-ttu-id="57f58-125">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="57f58-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="57f58-126">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="57f58-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="57f58-127">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="57f58-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f58-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57f58-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="57f58-129">Nasıl yapılır: Bir Windows Formdan Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="57f58-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="57f58-130">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="57f58-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
