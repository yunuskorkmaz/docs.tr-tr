---
title: 'Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 5f533d82fcca07a2b64bdbbfb160a7b2a23ce540
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592377"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a><span data-ttu-id="fbb67-102">Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme</span><span class="sxs-lookup"><span data-stu-id="fbb67-102">How to: Load a Sound Asynchronously within a Windows Form</span></span>
<span data-ttu-id="fbb67-103">Aşağıdaki kod örneği, zaman uyumsuz olarak bir ses bir URL'den yükler ve ardından yeni bir iş parçacığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fbb67-103">The following code example asynchronously loads a sound from an URL and then plays it on a new thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb67-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbb67-104">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbb67-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fbb67-105">Compiling the Code</span></span>  
 <span data-ttu-id="fbb67-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fbb67-106">This example requires:</span></span>  
  
- <span data-ttu-id="fbb67-107">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="fbb67-107">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="fbb67-108">Dosya adı yerine `"http://www.tailspintoys.com/sounds/stop.wav"` ile geçerli bir dosya adı.</span><span class="sxs-lookup"><span data-stu-id="fbb67-108">That you replace the file name `"http://www.tailspintoys.com/sounds/stop.wav"` with a valid file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fbb67-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fbb67-109">Robust Programming</span></span>  
 <span data-ttu-id="fbb67-110">Dosya işlemleri uygun özel durum işleme bloğu alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fbb67-110">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="fbb67-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="fbb67-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="fbb67-112">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="fbb67-112">The path name is malformed.</span></span> <span data-ttu-id="fbb67-113">Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-113">For example, it contains characters that are not valid or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
- <span data-ttu-id="fbb67-114">Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="fbb67-115">Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-115">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="fbb67-116">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="fbb67-117">Yol geçerli değil (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-117">The path is not valid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
- <span data-ttu-id="fbb67-118">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="fbb67-118">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbb67-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fbb67-119">.NET Framework Security</span></span>  
 <span data-ttu-id="fbb67-120">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="fbb67-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="fbb67-121">Örneğin, dosyayı `Form1.vb` Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fbb67-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="fbb67-122">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fbb67-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb67-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbb67-123">See also</span></span>

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [<span data-ttu-id="fbb67-124">Nasıl yapılır: Bir Windows formdan ses çalma</span><span class="sxs-lookup"><span data-stu-id="fbb67-124">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
