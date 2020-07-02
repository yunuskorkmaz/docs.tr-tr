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
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Nasıl yapılır: Bir Windows Formdan Ses Çalma
Bu örnek, çalışma zamanında belirli bir yolda bir ses çalar.

## <a name="example"></a>Örnek

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

## <a name="compiling-the-code"></a>Kod Derleniyor
 Bu örnek şunları gerektirir:

- Dosya adını `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adıyla değiştirirsiniz.

- Þ <xref:System.Media?displayProperty=nameWithType>Ad alanına başvuru.

## <a name="robust-programming"></a>Güçlü Programlama
 Dosya işlemleri uygun yapılandırılmış özel durum işleme blokları içine alınmalıdır.

 Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> sınıf) içeriyor.

- Yol salt okunurdur ( <xref:System.IO.IOException> sınıf).

- Yol adı `null` ( <xref:System.ArgumentNullException> sınıf).

- Yol adı çok uzun ( <xref:System.IO.PathTooLongException> sınıf).

- Yol geçersiz ( <xref:System.IO.DirectoryNotFoundException> sınıf).

- Yol yalnızca bir iki nokta üst üste, ":" ( <xref:System.NotSupportedException> sınıf).

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya `Form1.vb` bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Media.SoundPlayer>
- [Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
