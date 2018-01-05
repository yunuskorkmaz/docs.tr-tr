---
title: "Nasıl yapılır: Bir Windows Formdan Ses Çalma"
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
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c9495e22af0e06869d54f02d4ce0e866e28dbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="b407f-102">Nasıl yapılır: Bir Windows Formdan Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="b407f-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="b407f-103">Bu örnek, çalışma zamanında verilen yolda bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="b407f-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b407f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b407f-104">Example</span></span>  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b407f-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b407f-105">Compiling the Code</span></span>  
 <span data-ttu-id="b407f-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b407f-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b407f-107">Dosya adı yerine `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adı ile.</span><span class="sxs-lookup"><span data-stu-id="b407f-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="b407f-108">(C#) Bir başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b407f-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b407f-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b407f-109">Robust Programming</span></span>  
 <span data-ttu-id="b407f-110">Dosya işlemleri blokları uygun yapılandırılmış özel durum işleme içinde içine alınması.</span><span class="sxs-lookup"><span data-stu-id="b407f-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="b407f-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b407f-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b407f-112">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="b407f-112">The path name is malformed.</span></span> <span data-ttu-id="b407f-113">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="b407f-114">Yolun salt okunurdur (<xref:System.IO.IOException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="b407f-115">Yol adı `null` (<xref:System.ArgumentNullException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="b407f-116">Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="b407f-117">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="b407f-118">Yalnızca bir iki nokta üst üste, yoludur ":" (<xref:System.NotSupportedException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="b407f-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b407f-119">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b407f-119">.NET Framework Security</span></span>  
 <span data-ttu-id="b407f-120">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="b407f-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b407f-121">Örneğin, dosya `Form1.vb` bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b407f-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="b407f-122">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b407f-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b407f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b407f-123">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="b407f-124">Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme</span><span class="sxs-lookup"><span data-stu-id="b407f-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
