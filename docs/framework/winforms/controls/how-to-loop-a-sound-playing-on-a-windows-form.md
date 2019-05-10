---
title: 'Nasıl yapılır: Windows Form Üzerinde Bir Çalma Sesini Döngüye Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: bc3cf7775f68237f8b3393f867b81fcf020e52fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649287"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="a9720-102">Nasıl yapılır: Windows Form Üzerinde Bir Çalma Sesini Döngüye Alma</span><span class="sxs-lookup"><span data-stu-id="a9720-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="a9720-103">Aşağıdaki kod örneği, sürekli bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="a9720-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="a9720-104">Zaman kodunda `stopPlayingButton_Click` olay işleyicisi çalıştığında, herhangi bir sesi durdurur yürütülmekte.</span><span class="sxs-lookup"><span data-stu-id="a9720-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="a9720-105">Ses çalma, hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="a9720-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9720-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9720-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9720-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a9720-107">Compiling the Code</span></span>  
 <span data-ttu-id="a9720-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a9720-108">This example requires:</span></span>  
  
- <span data-ttu-id="a9720-109">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="a9720-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="a9720-110">Dosya adı yerine `"c:\Windows\Media\chimes.wav"` ile geçerli bir dosya adı.</span><span class="sxs-lookup"><span data-stu-id="a9720-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="a9720-111">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9720-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a9720-112">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9720-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a9720-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a9720-113">Robust Programming</span></span>  
 <span data-ttu-id="a9720-114">Dosya işlemleri uygun özel durum işleme bloğu alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9720-114">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="a9720-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="a9720-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a9720-116">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="a9720-116">The path name is malformed.</span></span> <span data-ttu-id="a9720-117">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk olan (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-117">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="a9720-118">Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-118">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="a9720-119">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-119">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="a9720-120">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-120">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="a9720-121">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-121">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="a9720-122">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="a9720-122">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a9720-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a9720-123">.NET Framework Security</span></span>  
 <span data-ttu-id="a9720-124">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="a9720-124">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="a9720-125">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a9720-125">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="a9720-126">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a9720-126">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9720-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9720-127">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="a9720-128">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="a9720-128">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="a9720-129">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a9720-129">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
