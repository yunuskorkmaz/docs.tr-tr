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
ms.openlocfilehash: 1d710f1e6d3b208365d5b1eb2524fbeeaa673c2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185763"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>Nasıl yapılır: Bir Windows Form içinde Zaman Uyumsuz Ses Yükleme
Aşağıdaki kod örneği, zaman uyumsuz olarak bir ses bir URL'den yükler ve ardından yeni bir iş parçacığında yürütülür.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
-   Dosya adı yerine `"http://www.tailspintoys.com/sounds/stop.wav"` ile geçerli bir dosya adı.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dosya işlemleri uygun özel durum işleme bloğu alınmalıdır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yol adı yanlış biçimlendirilmiş. Örneğin, geçerli olmayan karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı).  
  
-   Salt okunur yoludur (<xref:System.IO.IOException> sınıfı).  
  
-   Yol adı `Nothing` (<xref:System.ArgumentNullException> sınıfı).  
  
-   Yol adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
-   Yol geçerli değil (<xref:System.IO.DirectoryNotFoundException> sınıfı).  
  
-   Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosyayı `Form1.vb` Visual Basic kaynak dosyası olmayabilir. Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [Nasıl yapılır: Bir Windows formdan ses çalma](how-to-play-a-sound-from-a-windows-form.md)
