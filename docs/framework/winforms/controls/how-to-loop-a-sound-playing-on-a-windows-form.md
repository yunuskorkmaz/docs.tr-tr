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
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Nasıl yapılır: Windows Form Üzerinde Bir Çalma Sesini Döngüye Alma
Aşağıdaki kod örneği, sürekli bir ses çalar. Zaman kodunda `stopPlayingButton_Click` olay işleyicisi çalıştığında, herhangi bir sesi durdurur yürütülmekte. Ses çalma, hiçbir şey olmaz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
- Dosya adı yerine `"c:\Windows\Media\chimes.wav"` ile geçerli bir dosya adı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya işlemleri uygun özel durum işleme bloğu alınmalıdır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol adı yanlış biçimlendirilmiş. Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk olan (<xref:System.ArgumentException> sınıfı).  
  
- Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).  
  
- Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).  
  
- Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
- Yol geçersiz (<xref:System.IO.DirectoryNotFoundException> sınıfı).  
  
- Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası bir Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [Nasıl yapılır: Bir Windows formdan ses çalma](how-to-play-a-sound-from-a-windows-form.md)
- [SoundPlayer Sınıfına Genel Bakış](soundplayer-class-overview.md)
