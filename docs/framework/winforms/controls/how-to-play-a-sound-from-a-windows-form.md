---
title: 'Nasıl yapılır: Bir Windows Formdan Ses Çalma'
description: Çalışma zamanında belirli bir yoldaki bir Windows formdan ses yürütme hakkında bilgi edinin. Ayrıca, kodu ve .NET güvenlik çerçevesini derleme hakkında bilgi edinin.
ms.date: 03/30/2017
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
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613754"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="e338e-104">Nasıl yapılır: Bir Windows Formdan Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="e338e-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="e338e-105">Bu örnek, çalışma zamanında belirli bir yolda bir ses çalar.</span><span class="sxs-lookup"><span data-stu-id="e338e-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="e338e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e338e-106">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="e338e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e338e-107">Compiling the Code</span></span>
 <span data-ttu-id="e338e-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e338e-108">This example requires:</span></span>

- <span data-ttu-id="e338e-109">Dosya adını `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adıyla değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e338e-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="e338e-110">Þ <xref:System.Media?displayProperty=nameWithType>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="e338e-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="e338e-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e338e-111">Robust Programming</span></span>
 <span data-ttu-id="e338e-112">Dosya işlemleri uygun yapılandırılmış özel durum işleme blokları içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e338e-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="e338e-113">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="e338e-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e338e-114">Yol adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e338e-114">The path name is malformed.</span></span> <span data-ttu-id="e338e-115">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> sınıf) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e338e-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="e338e-116">Yol salt okunurdur ( <xref:System.IO.IOException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="e338e-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="e338e-117">Yol adı `null` ( <xref:System.ArgumentNullException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="e338e-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="e338e-118">Yol adı çok uzun ( <xref:System.IO.PathTooLongException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="e338e-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="e338e-119">Yol geçersiz ( <xref:System.IO.DirectoryNotFoundException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="e338e-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="e338e-120">Yol yalnızca bir iki nokta üst üste, ":" ( <xref:System.NotSupportedException> sınıf).</span><span class="sxs-lookup"><span data-stu-id="e338e-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="e338e-121">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e338e-121">.NET Framework Security</span></span>
 <span data-ttu-id="e338e-122">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="e338e-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e338e-123">Örneğin, dosya `Form1.vb` bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e338e-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="e338e-124">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e338e-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="e338e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e338e-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="e338e-126">Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme</span><span class="sxs-lookup"><span data-stu-id="e338e-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
