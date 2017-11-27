---
title: "Visual Basic'de Dizi Boyutları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a>Visual Basic'de Dizi Boyutları
A *boyut* içinde gösterebilir bir dizinin öğelerini belirtimi bir yönüdür. Satış her ay gün için toplam tutan bir dizi bir boyut (ayın günü) sahiptir. Satış toplam bölüm tarafından her ayın için tutan bir dizi (bölüm numarası ve ayın günü) iki boyutu vardır. Bir dizisi olduğundan dimensions sayısı adlı kendi *derece*.  
  
> [!NOTE]
>  Kullanabileceğiniz <xref:System.Array.Rank%2A> kaç boyutları bir dizisi olduğundan belirlemek için özellik.  
  
## <a name="working-with-dimensions"></a>Boyutlarıyla çalışma  
 Sağlayarak bir dizi bir öğe belirtin bir *dizin* veya *alt simge* her boyutları. Her boyut bitişik o boyutu için en yüksek dizin aracılığıyla 0 dizinden öğelerdir.  
  
 Aşağıdaki çizimler farklı sıralar dizilerle kavramsal yapısını göstermektedir. Her bir öğesinde çizimler erişim dizin değerleri gösterir. Örneğin, ikinci satırın iki boyutlu dizinin ilk öğesi dizinleri belirterek erişebileceğiniz `(1, 0)`.  
  
 ![Bir &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")  
Tek boyutlu dizi  
  
 ![İki &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")  
İki boyutlu dizi  
  
 ![Üç &#45;grafik diyagramı; boyutlu bir dizi](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")  
Üç boyutlu dizi  
  
### <a name="one-dimension"></a>Bir boyut  
 Birçok diziler her yaş kişiler sayısı gibi yalnızca bir boyuta sahip. Bu öğe sayısı tutan yaş yalnızca bir öğe belirtin gereksinimdir. Bu nedenle, bu tür bir dizi yalnızca bir dizin kullanır. Aşağıdaki örnek tutmak için bir değişken bildiren bir *tek boyutlu dizi* yaş 0 ile 120 için yaşını sayar.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>İki boyutu  
 Bazı diziler iki boyutları, her bir yerleşkede oluşturmanın her aşamasında ofisleri sayısı gibi sahip. Bir öğenin belirtimi bina numarasını ve kat gerektirir ve her öğe sayısı bina ve kat birleşimi için tutar. Bu nedenle, bu tür bir dizi iki dizin kullanır. Aşağıdaki örnek tutmak için bir değişken bildiren bir *iki boyutlu dizi* office sayısının binalar 0 ile 40 ve Katlar 0 ile 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 İki boyutlu bir dizi olarak da adlandırılan bir *dikdörtgen dizi*.  
  
### <a name="three-dimensions"></a>Üç boyut  
 Birkaç diziler üç boyutlu alan değerleri gibi üç boyut sahip. Bu tür bir dizi bu durumda x, y ve fiziksel alan z koordinatları temsil üç dizin kullanır. Aşağıdaki örnek tutmak için bir değişken bildiren bir *üç boyutlu dizi* , üç boyutlu bir birim çeşitli yerlerinde hava etme.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Birden fazla üç boyut  
 Bir dizi olarak en fazla 32 boyutları sahip olabilirsiniz, ancak en fazla üç sahip nadir.  
  
> [!NOTE]
>  Bir dizi boyutları eklediğinizde, toplam depolama dizisi tarafından gereken önemli ölçüde, bunu kullanmak çok boyutlu diziler dikkatli artırır.  
  
## <a name="using-different-dimensions"></a>Farklı boyutları kullanma  
 Her ayın mevcut için satış tutarlarının izlemek istediğinizi varsayalım. Aşağıdaki örnek olarak ayın her günü için gösterir tek boyutlu dizi 31 öğelerle bildirme.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Şimdi, aynı bilgileri, her gün için yalnızca bir ay aynı zamanda yılın her ay için izlemek istediğiniz varsayalım. Aşağıdaki örnekte gösterildiği gibi iki boyutlu bir dizi 12 satırlar (ay için) ve (gündür), 31 sütunlarla bildirme.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Şimdi sahip karar varsayalım bilgi birden fazla bir yıl için dizinizi tutun. Satış tutarlarının 5 yıl boyunca izlemek isterseniz, aşağıdaki örnekte gösterildiği gibi üç boyutlu bir dizi 5 katmanlar, 12 satırları ve 31 sütunlarla bildirebilirsiniz.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Her dizin, en çok her boyutu 0'dan değiştiğinden, Not `salesAmounts` o boyut için bir gerekli uzunluğundan daha az olarak bildirilmedi. Ayrıca, dizi boyutu her yeni bir boyut ile artar unutmayın. Üç önceki örneklerde 31, 372 ve 1,860 öğeleri sırasıyla boyutlarıdır.  
  
> [!NOTE]
>  Bir dizi kullanmadan oluşturabileceğiniz `Dim` deyimi veya `New` yan tümcesi. Örneğin, çağırabilirsiniz <xref:System.Array.CreateInstance%2A> yöntemi ya da başka bir bileşen iletebilir kodunuzu bu şekilde oluşturulan bir dizi. Bu tür bir dizi alt sınırı 0'dan farklı olabilir. Kullanarak her zaman bir boyutun alt sınır için bir test edebilirsiniz <xref:System.Array.GetLowerBound%2A> yöntemi veya `LBound` işlevi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dizilerle ilgili sorun giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
