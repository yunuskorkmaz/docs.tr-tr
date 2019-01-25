---
title: Dizilerle İlgili Sorun Giderme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 81817af230298528a766aa6494899538c35da7bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707628"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Dizilerle İlgili Sorun Giderme (Visual Basic)
Bu sayfada dizilerle çalışırken ortaya çıkabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Derleme hataları bildirme ve bir dizi başlatma  
 Yanlış anlama bildirme, oluşturma ve dizileri başlatma kurallarını, gelen derleme hataları oluşabilir. Hataların en yaygın nedenleri şunlardır:  
  
-   Sağlama bir [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) boyutun uzunluğu dizi değişken bildiriminde belirttikten sonra yan tümcesi. Aşağıdaki kod satırları bu türünde geçersiz bildirimi gösterir.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Birden çok basit bir dizi en üst düzey dizi boyut uzunlukları belirtme. Aşağıdaki kod satırı, bu tür geçersiz bir bildirimi gösterir.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Atlama `New` öğe değerlerini belirlerken anahtar sözcüğü. Aşağıdaki kod satırı, bu tür geçersiz bir bildirimi gösterir.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Sağlama bir `New` yan tümcesi küme ayraçları olmadan (`{}`). Aşağıdaki kod satırları bu türünde geçersiz bildirimi gösterir.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Bir dizi je mimo rozsah erişme  
 Dizi başlatma işlemi, her boyut için üst limit ve alt sınırı atar. Her bir öğe dizinin erişim, geçerli dizin veya her boyut için alt simge belirtmeniz gerekir. Herhangi bir dizini altında kendi alt sınır veya üst sınır, yukarıda ise bir <xref:System.IndexOutOfRangeException> özel durum sonuçları. Çalışma zamanında bir hata oluşmaz derleyici bu tür bir hataya algılayamaz.  
  
### <a name="determining-bounds"></a>Sınırları belirleme  
 Başka bir bileşen, kodunuzu bir dizi geçerse, örneğin bir yordam bağımsız değişken olarak, bu dizinin boyutu veya boyutlarının uzunluklarının bilmezsiniz. Herhangi bir öğe erişmeye çalışmadan önce her zaman bir dizinin her boyutunun üst sınırını belirlemeniz gerekir. Dizi dışındaki bir Visual Basic bazı yollarla oluşturulduysa `New` yan tümcesi alt sınırı 0 dışında bir şey olabilir ve de bu alt sınır belirlemek en güvenlisidir.  
  
### <a name="specifying-the-dimension"></a>Boyut belirtme  
 Çok boyutlu bir dizinin sınırları belirlerken, boyut nasıl belirttiğiniz ilgileniriz. `dimension` Parametrelerinin <xref:System.Array.GetLowerBound%2A> ve <xref:System.Array.GetUpperBound%2A> yöntemleri 0 tabanlıdır; çalışırken `Rank` Visual Basic parametrelerinin <xref:Microsoft.VisualBasic.Information.LBound%2A> ve <xref:Microsoft.VisualBasic.Information.UBound%2A> işlevleri 1 tabanlı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
