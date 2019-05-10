---
title: 'Nasıl yapılır: Bir Windows Formdan Ses Çalma'
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
ms.openlocfilehash: 8c70187948577064ab2471e2263e587035c41754
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662402"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Nasıl yapılır: Bir Windows Formdan Ses Çalma
Bu örnek, çalışma zamanında verilen yolda bir ses çalar.  
  
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
 Bu örnek gerektirir:  
  
- Dosya adı yerine `"c:\Windows\Media\chimes.wav"` ile geçerli bir dosya adı.  
  
- (C#) Başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya işlemleri blokları uygun yapılandırılmış özel durum işleme içinde içine alınması.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).  
  
- Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).  
  
- Yol adı `null` (<xref:System.ArgumentNullException> sınıfı).  
  
- Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
- Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).  
  
- Yalnızca bir iki nokta üst üste, yoludur ":" (<xref:System.NotSupportedException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosyayı `Form1.vb` Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Media.SoundPlayer>
- [Nasıl yapılır: Bir Windows Form içinde zaman uyumsuz ses yükleme](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
