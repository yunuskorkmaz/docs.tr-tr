---
title: Nesne Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415589"
---
# <a name="object-data-type"></a>Nesne Veri Türü

Nesnelere başvuran adresleri tutar. Herhangi bir başvuru türünü (String, Array, Class veya Interface) bir `Object` değişkene atayabilirsiniz. Bir `Object` değişken, herhangi bir değer türünün (sayısal, `Boolean` , `Char` ,, `Date` Yapı veya sabit listesi) verilerine de başvurabilir.

## <a name="remarks"></a>Açıklamalar

`Object`Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere herhangi bir veri türünün verilerini işaret edebilir. `Object`Derleme zamanında, değişkenin işaret edebilecekleri veri türünü bilmediğinizde ' i kullanın.

Öğesinin varsayılan değeri `Object` `Nothing` (null başvurusu).

## <a name="data-types"></a>Veri Türleri

Bir değişkene herhangi bir veri türü için değişken, sabit veya ifade atayabilirsiniz `Object` . Şu anda başvurduğu bir değişkenin veri türünü öğrenmek için `Object` , <xref:System.Type.GetTypeCode%2A> sınıfının yöntemini kullanabilirsiniz <xref:System.Type?displayProperty=nameWithType> . Aşağıdaki örnek bunu göstermektedir.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object`Veri türü bir başvuru türüdür. Ancak, Visual Basic bir `Object` değişkeni bir değer türünün verilerine başvurduğunda değer türü olarak değerlendirir.

## <a name="storage"></a>Depolama

Başvurduğu veri türü ne olursa olsun, bir `Object` değişken veri değerinin kendisini içermez, bunun yerine değer için bir işaretçi. Bilgisayar belleğinde her zaman dört bayt kullanır, ancak bu, değişkenin değerini temsil eden veriler için depolama alanı içermez. Verileri bulmak için işaretçiyi kullanan kod nedeniyle, `Object` değer türlerini tutan değişkenlerin açık olarak belirlenmiş değişkenlerle erişimi biraz daha yavaştır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabiriminiz varsa, diğer ortamlardaki işaretçi türlerinin Visual Basic türüyle uyumlu olmadığını göz önünde bulundurun `Object` .

- **Mının.** Türü ile bildirdiğiniz bir değişken, `Object` herhangi bir nesneye başvuru içermesi için yeterince esnektir. Ancak, bu tür bir değişkende bir yöntemi veya özelliği çağırdığınızda, her zaman *geç bağlamaya* (çalışma zamanında) tabi olursunuz. *Erken bağlamayı* zorlamak için (derleme zamanında) ve daha iyi performans, değişkeni belirli bir sınıf adıyla bildirin veya belirli bir veri türüne atayın.

  Bir nesne değişkeni bildirdiğinizde, örneğin Genelleştirilmiş tür yerine belirli bir sınıf türü kullanmayı deneyin <xref:System.OperatingSystem> `Object` . <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control> Özelliklerine ve yöntemlerine erişebilmek için, yerine, kullanılabilir olan en özel sınıfı da kullanmanız gerekir. Kullanılabilir sınıf adlarını bulmak için genellikle **nesne tarayıcısı** **sınıfları** listesini kullanabilirsiniz.

- **Kan.** Tüm veri türleri ve tüm başvuru türleri veri türüne göre genişledir `Object` . Bu, herhangi `Object` bir türü bir hatayla karşılaşmadan dönüştürmek üzere dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

  Ancak, değer türleri arasında dönüştürme yaparsanız `Object` , Visual Basic, yürütmeyi daha yavaş hale getiren *kutulama* ve *kutudan*çıkarma adlı işlemleri gerçekleştirir.

- **Tür karakterleri.** `Object`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıftır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Object` bir nesne örneğine işaret eden bir değişken gösterir.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
