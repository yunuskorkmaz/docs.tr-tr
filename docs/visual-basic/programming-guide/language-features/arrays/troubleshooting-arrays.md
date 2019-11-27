---
title: Dizilerle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349074"
---
# <a name="troubleshooting-arrays-visual-basic"></a>Dizilerle İlgili Sorun Giderme (Visual Basic)
Bu sayfada, dizilerle çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Bir diziyi bildiren ve başlatarak derleme hataları  
 Derleme hataları, dizileri bildirmek, oluşturmak ve başlatmak için kuralların yanlış anlaşılmasından kaynaklanabilir. Hataların en yaygın nedenleri şunlardır:  
  
- Dizi değişkeni bildiriminde boyut uzunluklarını belirttikten sonra [Yeni bir işleç](../../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi sağlama. Aşağıdaki kod satırları bu türün geçersiz bildirimlerini gösterir.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- Pürüzlü bir dizinin en üst düzey dizisinden daha fazla boyut uzunluğu belirtme. Aşağıdaki kod satırı, bu türün geçersiz bir bildirimini gösterir.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- Öğe değerlerini belirtirken `New` anahtar sözcüğünü atlama. Aşağıdaki kod satırı, bu türün geçersiz bir bildirimini gösterir.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- Küme ayracı olmadan bir `New` yan tümcesi sağlama (`{}`). Aşağıdaki kod satırları bu türün geçersiz bildirimlerini gösterir.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Dizi sınırların dışına erişme  
 Bir diziyi başlatma işlemi, her boyuta bir üst sınır ve alt sınır atar. Dizi öğesine her erişim için her boyut için geçerli bir dizin veya alt simge belirtilmelidir. Herhangi bir dizin alt sınırının altında veya üst sınırının üstünde olursa, <xref:System.IndexOutOfRangeException> özel durum oluşur. Derleyici bu tür bir hatayı algılayamazsınız, bu nedenle çalışma zamanında bir hata oluşur.  
  
### <a name="determining-bounds"></a>Sınırları belirleme  
 Başka bir bileşen kodunuza bir dizi geçirirse (örneğin, bir yordam bağımsız değişkeni olarak), bu dizinin boyutunu veya boyutlarının uzunluğunu bilemezsiniz. Herhangi bir öğeye erişmeyi denemeden önce her zaman bir dizinin her boyutu için üst sınırı belirlemelisiniz. Dizi Visual Basic `New` yan tümcesi dışında bazı yollarla oluşturulduysa, alt sınır 0 dışında bir değer olabilir ve bu alt sınırın de belirlenmesi en güvenli hale gelir.  
  
### <a name="specifying-the-dimension"></a>Boyut belirtme  
 Çok boyutlu bir dizinin sınırlarını belirlerken, boyutu nasıl belirteceğini dikkatli yapın. <xref:System.Array.GetLowerBound%2A> ve <xref:System.Array.GetUpperBound%2A> yöntemlerinin `dimension` parametreleri 0 tabanlıdır, ancak Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> `Rank` parametreleri ve <xref:Microsoft.VisualBasic.Information.UBound%2A> işlevleri 1 tabanlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nasıl yapılır: Visual Basic dizi değişkenini başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
