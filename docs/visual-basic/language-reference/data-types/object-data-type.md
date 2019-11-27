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
ms.openlocfilehash: 2ccb9b69b865c259d078ed9642d63c7f83514756
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343961"
---
# <a name="object-data-type"></a>Nesne Veri Türü

Nesnelere başvuran adresleri tutar. Bir `Object` değişkenine herhangi bir başvuru türü (dize, dizi, sınıf veya arabirim) atayabilirsiniz. `Object` değişken, herhangi bir değer türü (sayısal, `Boolean`, `Char`, `Date`, yapı veya numaralandırma) verilerine de başvurabilir.

## <a name="remarks"></a>Açıklamalar

`Object` veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere herhangi bir veri türünün verilerini işaret edebilir. Değişkenin işaret edebilecekleri veri türünü derleme sırasında bilmediğinizde `Object` kullanın.

`Object` varsayılan değeri `Nothing` (null başvuru).

## <a name="data-types"></a>Veri Türleri

Bir `Object` değişkenine herhangi bir veri türü için değişken, sabit veya ifade atayabilirsiniz. Şu anda başvurduğu bir `Object` değişkeni veri türünü öğrenmek için <xref:System.Type?displayProperty=nameWithType> sınıfının <xref:System.Type.GetTypeCode%2A> yöntemini kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object` veri türü bir başvuru türüdür. Ancak Visual Basic, bir değer türünün verilerine başvurduğu zaman bir `Object` değişkenini değer türü olarak değerlendirir.

## <a name="storage"></a>Depolama

Başvurduğu veri türü ne olursa olsun, bir `Object` değişkeni veri değerinin kendisini içermez, ancak bu değer için bir işaretçi yerine. Bilgisayar belleğinde her zaman dört bayt kullanır, ancak bu, değişkenin değerini temsil eden veriler için depolama alanı içermez. Verileri bulmak için işaretçiyi kullanan kod nedeniyle, değer türlerini tutan `Object` değişkenleri açıkça yazılmış değişkenlerle daha yavaş erişime biraz daha yavaştır.

## <a name="programming-tips"></a>Programlama İpuçları

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabiriminiz varsa, diğer ortamlardaki işaretçi türlerinin Visual Basic `Object` türüyle uyumlu olmadığını aklınızda bulundurun.

- **Mının.** `Object` türü ile bildirdiğiniz bir değişken, herhangi bir nesneye başvuru içermesi için yeterince esnektir. Ancak, bu tür bir değişkende bir yöntemi veya özelliği çağırdığınızda, her zaman *geç bağlamaya* (çalışma zamanında) tabi olursunuz. *Erken bağlamayı* zorlamak için (derleme zamanında) ve daha iyi performans, değişkeni belirli bir sınıf adıyla bildirin veya belirli bir veri türüne atayın.

  Bir nesne değişkeni bildirdiğinizde, genelleştirilmiş `Object` türü yerine belirli bir sınıf türü kullanmayı deneyin, örneğin <xref:System.OperatingSystem>. Özelliklerine ve yöntemlerine erişebilmek için, <xref:System.Windows.Forms.Control>yerine <xref:System.Windows.Forms.TextBox> gibi en özel sınıfı da kullanmanız gerekir. Kullanılabilir sınıf adlarını bulmak için genellikle **nesne tarayıcısı** **sınıfları** listesini kullanabilirsiniz.

- **Kan.** Tüm veri türleri ve tüm başvuru türleri `Object` veri türüne göre genişledir. Bu, bir <xref:System.OverflowException?displayProperty=nameWithType> hatasıyla karşılaşmadan herhangi bir türü `Object` dönüştürebileceğiniz anlamına gelir.

  Ancak, değer türleri ve `Object`arasında dönüştürme yaparsanız, Visual Basic, yürütmeyi daha yavaş hale getiren *kutulama* ve *kutudan*çıkarma adlı işlemleri gerçekleştirir.

- **Tür karakterleri.** `Object` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıfıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir nesne örneğine işaret eden bir `Object` değişkeni gösterilmektedir.

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
- [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
