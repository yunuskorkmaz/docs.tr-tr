---
title: "Dizilerle İlgili Sorun Giderme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a>Dizilerle İlgili Sorun Giderme (Visual Basic)
Bu sayfada dizilerle çalışırken ortaya çıkabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Bildirme ve bir dizi başlatma derleme hataları  
 Derleme hataları yanlış anlama bildirme, oluşturma ve dizileri başlatma kuralları, gelen ortaya çıkabilir. Hataların en yaygın nedenler şunlardır:  
  
-   Sağlama bir [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) dizi değişken bildiriminde boyut uzunlukları belirttikten sonra yan tümcesi. Aşağıdaki kod satırlarını bu tür geçersiz bildirimleri göster.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Birden çok basit bir dizinin en üst düzey dizi boyut uzunlukları belirtme. Aşağıdaki kod satırı bu tür geçersiz bir bildirim gösterilir.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Atlama `New` öğesi değerler belirtirken anahtar sözcüğü. Aşağıdaki kod satırı bu tür geçersiz bir bildirim gösterilir.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Sağlama bir `New` yan tümcesi olmadan küme ayraçları (`{}`). Aşağıdaki kod satırlarını bu tür geçersiz bildirimleri göster.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Bir dizinin sınırları dışında erişme  
 Bir dizi başlatma işleminin bir üst sınır alt sınır her boyut atamaktadır. Dizinin bir öğeye her erişim geçerli dizin ya da her boyut için indisi belirtmeniz gerekir. Bir dizin, alt sınır altında veya onun üst sınırının üzerinde ise bir <xref:System.IndexOutOfRangeException> özel durum sonuçları. Çalışma zamanında hata oluşmaz derleyici böyle bir hata algılayamaz.  
  
### <a name="determining-bounds"></a>Sınır belirleme  
 Başka bir bileşen kodunuzu bir dizi geçerse, örneğin bir yordam bağımsız değişken olarak, bu dizinin boyutu veya boyutlar uzunlukları bilmezsiniz. Herhangi bir öğe erişmeye çalışmadan önce her zaman bir dizinin her boyutu üst sınırı belirlemeniz gerekir. Dizi bazı yollarla dışında oluşturulup oluşturulmadığını bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` yan tümcesi, alt sınırı 0 dışında bir şey olabilir ve o alt sınır de belirlemek en güvenlisidir.  
  
### <a name="specifying-the-dimension"></a>Boyut belirtme  
 Çok boyutlu bir diziye sınırlarına belirlerken, boyutun nasıl belirttiğiniz dikkatli olun. `dimension` Parametrelerinin <xref:System.Array.GetLowerBound%2A> ve <xref:System.Array.GetUpperBound%2A> yöntemler 0 tabanlı, çalışırken `Rank` parametrelerinin [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> ve <xref:Microsoft.VisualBasic.Information.UBound%2A> işlevleri 1 tabanlı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
