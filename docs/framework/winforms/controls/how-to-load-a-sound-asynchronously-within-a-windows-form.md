---
title: 'Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme'
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
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea84f03088deb7225e90150d9d298f1b64030cc6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="e81f5-102">Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme</span><span class="sxs-lookup"><span data-stu-id="e81f5-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="e81f5-103">Aşağıdaki kod örneğinde zaman uyumsuz olarak bir URL'den ses yükler ve sonra yeni bir iş parçacığı üzerinde çalar.</span><span class="sxs-lookup"><span data-stu-id="e81f5-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e81f5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e81f5-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e81f5-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e81f5-105">Compiling the Code</span></span>  
 <span data-ttu-id="e81f5-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e81f5-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e81f5-107">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e81f5-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="e81f5-108">Dosya adı yerine `"http://www.tailspintoys.com/sounds/stop.wav"` geçerli bir dosya adı ile.</span><span class="sxs-lookup"><span data-stu-id="e81f5-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="e81f5-109">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e81f5-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e81f5-110">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e81f5-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e81f5-111">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e81f5-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e81f5-112">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e81f5-112">Robust Programming</span></span>  
 <span data-ttu-id="e81f5-113">Dosya işlemleri içinde uygun özel durum işleme blok içine alınması.</span><span class="sxs-lookup"><span data-stu-id="e81f5-113">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="e81f5-114">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="e81f5-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e81f5-115">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e81f5-115">The path name is malformed.</span></span> <span data-ttu-id="e81f5-116">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-116">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="e81f5-117">Yolun salt okunurdur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-117">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="e81f5-118">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-118">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="e81f5-119">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-119">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="e81f5-120">Yol geçerli değil (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-120">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="e81f5-121">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e81f5-121">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e81f5-122">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e81f5-122">.NET Framework Security</span></span>  
 <span data-ttu-id="e81f5-123">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="e81f5-123">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e81f5-124">Örneğin, dosya `Form1.vb` bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e81f5-124">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="e81f5-125">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e81f5-125">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81f5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e81f5-126">See Also</span></span>  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [<span data-ttu-id="e81f5-127">Nasıl yapılır: Bir Windows Formdan Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="e81f5-127">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
