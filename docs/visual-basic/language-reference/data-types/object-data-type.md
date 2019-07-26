---
title: Nesne veri türü (Visual Basic)
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
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513042"
---
# <a name="object-data-type"></a>Nesne Veri Türü

Nesnelere başvuran adresleri tutar. Herhangi bir başvuru türünü (String, Array, Class veya Interface) bir `Object` değişkene atayabilirsiniz. Bir `Object` değişken, herhangi bir değer türünün (sayısal, `Boolean`, `Char`, `Date`, yapı veya sabit listesi) verilerine de başvurabilir.

## <a name="remarks"></a>Açıklamalar

`Object` Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere herhangi bir veri türünün verilerini işaret edebilir. Derleme `Object` zamanında, değişkenin işaret edebilecekleri veri türünü bilmediğinizde ' i kullanın.

`Object` Öğesinin`Nothing` varsayılan değeri (null başvurusu).

## <a name="data-types"></a>Veri Türleri

Bir `Object` değişkene herhangi bir veri türü için değişken, sabit veya ifade atayabilirsiniz. Şu anda başvurduğu bir `Object` değişkenin veri türünü öğrenmek için, <xref:System.Type?displayProperty=nameWithType> sınıfının <xref:System.Type.GetTypeCode%2A> yöntemini kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object` Veri türü bir başvuru türüdür. Ancak, Visual Basic bir `Object` değişkeni bir değer türünün verilerine başvurduğunda değer türü olarak değerlendirir.

## <a name="storage"></a>Depolama

Başvurduğu veri türü ne olursa olsun, bir `Object` değişken veri değerinin kendisini içermez, bunun yerine değer için bir işaretçi. Bilgisayar belleğinde her zaman dört bayt kullanır, ancak bu, değişkenin değerini temsil eden veriler için depolama alanı içermez. Verileri bulmak için işaretçiyi kullanan kod nedeniyle, `Object` değer türlerini tutan değişkenlerin açık olarak belirlenmiş değişkenlerle erişimi biraz daha yavaştır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Birlikte çalışma konuları.** Otomasyon veya com nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabiriminiz varsa, diğer ortamlardaki işaretçi türlerinin Visual Basic `Object` türüyle uyumlu olmadığını göz önünde bulundurun.

- **Performans.** `Object` Türü ile bildirdiğiniz bir değişken, herhangi bir nesneye başvuru içermesi için yeterince esnektir. Ancak, bu tür bir değişkende bir yöntemi veya özelliği çağırdığınızda, her zaman *geç bağlamaya* (çalışma zamanında) tabi olursunuz. *Erken bağlamayı* zorlamak için (derleme zamanında) ve daha iyi performans, değişkeni belirli bir sınıf adıyla bildirin veya belirli bir veri türüne atayın.

  Bir nesne değişkeni bildirdiğinizde, örneğin <xref:System.OperatingSystem>Genelleştirilmiş `Object` tür yerine belirli bir sınıf türü kullanmayı deneyin. Özelliklerine ve yöntemlerine erişebilmek için, <xref:System.Windows.Forms.TextBox> yerine, kullanılabilir olan <xref:System.Windows.Forms.Control>en özel sınıfı da kullanmanız gerekir. Kullanılabilir sınıf adlarını bulmak için genellikle **nesne tarayıcısı** **sınıfları** listesini kullanabilirsiniz.

- **Kan.** Tüm veri türleri ve tüm başvuru türleri `Object` veri türüne göre genişledir. Bu, herhangi bir türü bir `Object` <xref:System.OverflowException?displayProperty=nameWithType> hatayla karşılaşmadan dönüştürmek üzere dönüştürebileceğiniz anlamına gelir.

  Ancak, değer türleri `Object`arasında dönüştürme yaparsanız, Visual Basic, yürütmeyi daha yavaş hale getiren *kutulama* ve *kutudan*çıkarma adlı işlemleri gerçekleştirir.

- **Tür karakterleri.** `Object`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıftır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir nesne `Object` örneğine işaret eden bir değişken gösterir.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Nasıl yapılır: Iki nesnenin Ilgili olup olmadığını belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: Iki nesnenin aynı olup olmadığını belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
