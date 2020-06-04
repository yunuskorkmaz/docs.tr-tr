---
title: Dizi Boyutları
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413110"
---
# <a name="array-dimensions-in-visual-basic"></a>Visual Basic'de Dizi Boyutları

*Boyut* , bir dizinin öğelerinin belirtimini değiştirebileceğiniz bir yöndir. Ayın her günü için satış toplamı tutan bir dizinin bir boyutu (ayın günü) vardır. Ayın her günü için departmanın satış toplamı tutan bir dizinin iki boyutu vardır (Departman numarası ve ayın günü). Bir dizinin sahip olduğu boyut sayısı *derece*olarak adlandırılır.

> [!NOTE]
> <xref:System.Array.Rank%2A>Bir dizinin kaç boyut olduğunu anlamak için özelliğini kullanabilirsiniz.

## <a name="working-with-dimensions"></a>Boyutlarla çalışma

Bir dizinin bir öğesini, boyutlarının her biri için bir *Dizin* veya *alt simge* sağlayarak belirtirsiniz. Öğeler, 0 dizininden bu boyut için en yüksek dizin arasındaki her bir boyut boyunca bitişik.

Aşağıdaki çizimler, farklı derecelendirilerle dizilerin kavramsal yapısını gösterir. Çizimlerde bulunan her öğe, ona erişen dizin değerlerini gösterir. Örneğin, dizinler belirterek iki boyutlu dizinin ikinci satırındaki ilk öğesine erişebilirsiniz `(1, 0)` .

![Tek boyutlu dizi gösteren diyagram.](./media/array-dimensions/one-dimensional-array.gif)

![İki boyutlu bir dizi gösteren diyagram.](./media/array-dimensions/two-dimensional-array.gif)

![Üç boyutlu bir diziyi gösteren diyagram.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a>Bir boyut

Birçok dizi, her bir yaş için kişi sayısı gibi yalnızca bir boyuta sahiptir. Bir öğeyi belirtmeye yönelik tek gereksinim, bu öğenin sayımı tutan yaşdır. Bu nedenle, bu tür bir dizi yalnızca bir dizin kullanır. Aşağıdaki örnek, 0 ile 120 arasındaki yaşlar için *tek boyutlu* bir yaş dizisi sayısı tutan bir değişken bildirir.

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a>İki boyut

Bazı diziler, kampüs üzerinde her binadaki her bir kata ait ofislerin sayısı gibi iki boyuta sahiptir. Bir öğenin belirtimi hem bina numarası hem de kat gerektirir ve her öğe bu derleme ve kat birleşiminin sayısını tutar. Bu nedenle, bu tür bir dizi iki dizin kullanır. Aşağıdaki örnek, 0 ile 40 arası binalar ve 0 ile 5 arasındaki katkılar için *iki boyutlu bir dizi* Office sayımlarını tutmak üzere bir değişken bildirir.

```vb
Dim officeCounts(40, 5) As Byte
```

İki boyutlu bir dizi *dikdörtgen dizi*olarak da adlandırılır.

### <a name="three-dimensions"></a>Üç boyut

Birkaç dizide üç boyutlu boşluk değerleri gibi üç boyut vardır. Böyle bir dizi üç dizin kullanır. Bu örnekte, fiziksel alanın x, y ve z koordinatları temsil eder. Aşağıdaki örnek, üç boyutlu bir birimin çeşitli noktalarında *üç boyutlu* bir hava sıcaklığı dizisini tutacak bir değişken bildirir.

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a>Üçten fazla boyut

Bir dizide en fazla 32 boyut olabilir, ancak üçten fazla olabilir.

> [!NOTE]
> Bir diziye boyut eklediğinizde, dizi için gereken toplam depolama alanı önemli ölçüde artar, bu nedenle çok boyutlu dizileri dikkatli kullanın.

## <a name="using-different-dimensions"></a>Farklı boyutlar kullanma

Mevcut ayın her gününde satış miktarlarını izlemek istediğinizi varsayalım. Aşağıdaki örnekte gösterildiği gibi, ayın her günü için bir tane olmak üzere 31 öğe içeren tek boyutlu bir dizi bildirebilirsiniz.

```vb
Dim salesAmounts(30) As Double
```

Şimdi yalnızca bir ayın her gününde değil, yılın her ayında aynı bilgileri izlemek istediğinizi varsayalım. Aşağıdaki örnekte gösterildiği gibi 12 satır (aylar için) ve 31 sütun (günler için) ile iki boyutlu bir dizi bildirebilirsiniz.

```vb
Dim salesAmounts(11, 30) As Double
```

Artık, dizi tutma bilgilerinizin bir yıldan daha fazla olması gerektiğine varsayın. 5 yıl boyunca satış tutarlarını izlemek isterseniz, aşağıdaki örnekte gösterildiği gibi 5 katman, 12 satır ve 31 sütunlu üç boyutlu bir dizi bildirebilirsiniz.

```vb
Dim salesAmounts(4, 11, 30) As Double
```

Her bir dizin 0 ' dan en büyük ' a değiştiğinden, her boyutun `salesAmounts` Bu boyut için gereken uzunluktan bir daha az olarak bildirildiği unutulmamalıdır. Ayrıca, dizi boyutunun her yeni boyutla arttığı unutulmamalıdır. Yukarıdaki örneklerde bulunan üç boyut sırasıyla 31, 372 ve 1.860 öğeleridir.

> [!NOTE]
> `Dim`Deyimi veya yan tümcesini kullanmadan bir dizi oluşturabilirsiniz `New` . Örneğin, <xref:System.Array.CreateInstance%2A> yöntemini çağırabilirsiniz ya da başka bir bileşen kodunuzu bu şekilde oluşturulan bir diziye geçirebilir. Böyle bir dizide 0 dışında bir alt sınır olabilir. Yöntemini veya işlevini kullanarak, boyutun alt sınır için her zaman test edebilirsiniz <xref:System.Array.GetLowerBound%2A> `LBound` .

## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](index.md)
- [Dizilerle İlgili Sorun Giderme](troubleshooting-arrays.md)
