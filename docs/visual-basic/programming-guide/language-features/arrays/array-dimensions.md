---
title: Visual Basic'de Dizi Boyutları
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053723"
---
# <a name="array-dimensions-in-visual-basic"></a>Visual Basic'de Dizi Boyutları
A *boyut* içinde değişebilir bir dizinin öğelerin belirtimini yön olduğundan. Ayın her günü için toplam satış tutan bir dizi bir boyut (ayın gününü) sahiptir. Satış toplam departmana göre ayın her günü için tutan bir dizi iki boyutlu (bölüm numarası ve ayın günü) sahiptir. Sahip bir dizi boyut sayısını çağrılır, *derece*.  
  
> [!NOTE]
>  Kullanabileceğiniz <xref:System.Array.Rank%2A> kaç boyutları bir dizi sahip olduğunu belirlemek için özellik.  
  
## <a name="working-with-dimensions"></a>Boyutlarla çalışma  
 Sağlayarak bir dizideki bir öğe belirttiğiniz bir *dizin* veya *alt simge* için her bir boyutundan. Bitişik her boyut için bu boyut en yüksek dizin 0 dizininden öğeleridir.  
  
 Aşağıdaki çizimler farklı sıralamalara sahip dizilerle kavramsal yapısını göstermektedir. Çizimler her öğenin erişim dizin değerlerini gösterir. Örneğin, ilk öğesi iki boyutlu bir dizinin ikinci satırın dizinleri belirterek erişebileceğiniz `(1, 0)`.  
  
 ![Tek boyutlu dizi gösteren diyagram.](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![İki boyutlu bir dizi gösteren diyagram.](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![Üç boyutlu bir dizi gösteren diyagram.](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>Bir boyut  
 Birçok dizileri her yaşında kişilerin sayısını gibi yalnızca bir boyutu vardır. Bir öğe belirtmek için tek gereksinim, o öğe sayısı tutan yaş olmasıdır. Bu nedenle, böyle bir dizi yalnızca bir dizin kullanır. Aşağıdaki örnek, tutacak bir değişken bildirir. bir *tek boyutlu dizi* yaşlar 0 ila 120 için yaşını hesaplar.  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>İki boyutlu  
 Bazı diziler ve sayıda ofis her aşamasında, her bir Kampüste oluşturma gibi iki boyutlu sahip. Hem bina numarasını hem de katı bir öğe belirtimi gerektirir ve her öğe bina ve kat birleşimi için tutar. Bu nedenle, böyle bir dizi iki dizin kullanır. Aşağıdaki örnek, tutacak bir değişken bildirir. bir *iki boyutlu dizi* office sayılarını, 0 ile 40 Binalar ve Katlar 0 ile 5.  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 İki boyutlu bir dizi olarak da adlandırılan bir *dikdörtgen dizi*.  
  
### <a name="three-dimensions"></a>Üç boyutlu  
 Birkaç diziler üç boyutlu alan değerleri gibi üç boyutlara sahip. Böyle bir dizi, bu durumda x, y ve z bu gruplar fiziksel alan koordinatlarını temsil eden üç dizin kullanır. Aşağıdaki örnek, tutacak bir değişken bildirir. bir *üç boyutlu dizi* hava Sıcaklıkların çeşitli noktalarında üç boyutlu bir birim.  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>Üçten fazla boyutları  
 Bir dizi 32 adede kadar boyutları olabilse de, en fazla üç sahip nadir olarak rastlanıyor.  
  
> [!NOTE]
>  Bir diziye boyutları eklediğinizde, dizi tarafından gereken toplam depolama alanı önemli ölçüde, bunu kullanmak çok boyutlu diziler dikkatli artırır.  
  
## <a name="using-different-dimensions"></a>Farklı boyutları kullanma  
 Mevcut ayın her günü için satış tutarları izlemek istediğinizi varsayalım. Aşağıdaki örnek, ayın her günü için gösterir 31 öğeleri içeren tek boyutlu bir dizi bildirin.  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 Artık her gün için yalnızca aynı bilgileri ayın aynı zamanda her bir yılın ayı izlemek istediğinizi varsayalım. Aşağıdaki örnekte gösterildiği gibi iki boyutlu bir dizi (ay için) 12 satır ve (gün) boyunca 31 sütunlarını bildirin.  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 Şimdi, karar varsayalım bilgi birden fazla bir yıl boyunca diziniz tutun. Satış rakamlarını 5 yıl boyunca izlemek istiyorsanız, aşağıdaki örnekte gösterildiği gibi üç boyutlu bir dizi 5 katmanları, 12 satırlar ve sütunlar 31 bildirebilirsiniz.  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 Her dizin, en fazla her boyutunun 0'dan değiştiğinden, Not `salesAmounts` o boyut için gerekli uzunluğundan küçük olarak bildirilir. Ayrıca dizinin boyutu ile her yeni boyut arttığına dikkat edin. Önceki örneklerde üç boyut 31 372 ve 1,860 öğeleri sırasıyla.  
  
> [!NOTE]
>  Kullanmadan bir dizi oluşturabilirsiniz `Dim` deyimi veya `New` yan tümcesi. Örneğin, çağırabilirsiniz <xref:System.Array.CreateInstance%2A> yöntemi veya başka bir bileşen geçirebilirsiniz kodunuzu bu şekilde oluşturulan bir dizi. Böyle bir dizi alt sınırı 0'dan farklı olabilir. Bir boyut için alt sınırı kullanarak her zaman test edebilirsiniz <xref:System.Array.GetLowerBound%2A> yöntemi veya `LBound` işlevi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Dizilerle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
