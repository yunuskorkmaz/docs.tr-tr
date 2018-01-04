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
  
-   Dosya adı yerine `"c:\Windows\Media\chimes.wav"` geçerli bir dosya adı ile.  
  
-   (C#) Bir başvuru <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya işlemleri blokları uygun yapılandırılmış özel durum işleme içinde içine alınması.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).  
  
-   Yolun salt okunurdur (<xref:System.IO.IOException> sınıfı).  
  
-   Yol adı `null` (<xref:System.ArgumentNullException> sınıfı).  
  
-   Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
-   Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).  
  
-   Yalnızca bir iki nokta üst üste, yoludur ":" (<xref:System.NotSupportedException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya `Form1.vb` bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Media.SoundPlayer>  
 [Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
