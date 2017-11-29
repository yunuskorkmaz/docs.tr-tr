---
title: "Nasıl yapılır: Bir Windows Formda Sesi Döngü Olarak Çalma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e61a15a7a249a90ce9eca035ebe6fd67275bb74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="1d630-102">Nasıl yapılır: Bir Windows Formda Sesi Döngü Olarak Çalma</span><span class="sxs-lookup"><span data-stu-id="1d630-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="1d630-103">Aşağıdaki kod örneğinde ses sürekli olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="1d630-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="1d630-104">Olduğunda kodda `stopPlayingButton_Click` olay işleyicisi çalışır, durakları oynatılmakta ses.</span><span class="sxs-lookup"><span data-stu-id="1d630-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="1d630-105">Ses çalma, hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="1d630-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d630-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d630-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d630-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1d630-107">Compiling the Code</span></span>  
 <span data-ttu-id="1d630-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1d630-108">This example requires:</span></span>  
  
-   <span data-ttu-id="1d630-109">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1d630-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="1d630-110">Dosya adı yerine `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adı ile.</span><span class="sxs-lookup"><span data-stu-id="1d630-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="1d630-111">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1d630-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1d630-112">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="1d630-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1d630-113">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1d630-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d630-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1d630-114">Robust Programming</span></span>  
 <span data-ttu-id="1d630-115">Dosya işlemleri içinde uygun özel durum işleme blok içine alınması.</span><span class="sxs-lookup"><span data-stu-id="1d630-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="1d630-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="1d630-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1d630-117">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="1d630-117">The path name is malformed.</span></span> <span data-ttu-id="1d630-118">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk olan (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="1d630-119">Yolun salt okunurdur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="1d630-120">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="1d630-121">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="1d630-122">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="1d630-123">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1d630-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1d630-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1d630-124">.NET Framework Security</span></span>  
 <span data-ttu-id="1d630-125">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="1d630-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="1d630-126">Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d630-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="1d630-127">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1d630-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d630-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d630-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="1d630-129">Nasıl yapılır: bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="1d630-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="1d630-130">SoundPlayer sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="1d630-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
