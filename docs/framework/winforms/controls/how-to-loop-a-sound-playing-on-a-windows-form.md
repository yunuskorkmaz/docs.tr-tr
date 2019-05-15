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
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592366"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="1e8e3-102">Nasıl yapılır: Windows Form Üzerinde Bir Çalma Sesini Döngüye Alma</span><span class="sxs-lookup"><span data-stu-id="1e8e3-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="1e8e3-103">Aşağıdaki kod örneği, sürekli bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="1e8e3-104">Zaman kodunda `stopPlayingButton_Click` olay işleyicisi çalıştığında, herhangi bir sesi durdurur yürütülmekte.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="1e8e3-105">Ses çalma, hiçbir şey olmaz.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e8e3-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e8e3-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e8e3-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1e8e3-107">Compiling the Code</span></span>  
 <span data-ttu-id="1e8e3-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1e8e3-108">This example requires:</span></span>  
  
- <span data-ttu-id="1e8e3-109">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="1e8e3-110">Dosya adı yerine `"c:\Windows\Media\chimes.wav"` ile geçerli bir dosya adı.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1e8e3-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1e8e3-111">Robust Programming</span></span>  
 <span data-ttu-id="1e8e3-112">Dosya işlemleri uygun özel durum işleme bloğu alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-112">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="1e8e3-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="1e8e3-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1e8e3-114">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-114">The path name is malformed.</span></span> <span data-ttu-id="1e8e3-115">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk olan (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-115">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="1e8e3-116">Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="1e8e3-117">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-117">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="1e8e3-118">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="1e8e3-119">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="1e8e3-120">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="1e8e3-120">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1e8e3-121">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1e8e3-121">.NET Framework Security</span></span>  
 <span data-ttu-id="1e8e3-122">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="1e8e3-123">Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-123">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="1e8e3-124">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-124">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8e3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8e3-125">See also</span></span>

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [<span data-ttu-id="1e8e3-126">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="1e8e3-126">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="1e8e3-127">SoundPlayer Sınıfına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1e8e3-127">SoundPlayer Class Overview</span></span>](soundplayer-class-overview.md)
