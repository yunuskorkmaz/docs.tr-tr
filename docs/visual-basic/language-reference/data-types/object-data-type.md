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
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835576"
---
# <a name="object-data-type"></a>Nesne Veri Türü
Nesnelere atıfta adresleri tutar. Herhangi bir başvuru türü (dize, dizi, sınıf veya arabirim) atayabileceğiniz bir `Object` değişkeni. Bir `Object` değişkeni ayrıca herhangi bir değer türünün veri başvuru (sayısal, `Boolean`, `Char`, `Date`, yapı ya da numaralandırma).  
  
## <a name="remarks"></a>Açıklamalar  
 `Object` Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneğine dahil olmak üzere, herhangi bir veri türü veri işaret edebilir. Kullanım `Object` derleme zamanında bilmediğinizde değişkeni hangi veri türü için işaret ediyor olabilir.  
  
 Varsayılan değer olan `Object` olduğu `Nothing` (null bir başvuru).  
  
## <a name="data-types"></a>Veri Türleri  
 Bir değişken, sabit veya herhangi bir veri türü ifadesi atayabilirsiniz bir `Object` değişkeni. Veri türünü belirlemek için bir `Object` değişkeni şu anda başvurur, kullanabileceğiniz <xref:System.Type.GetTypeCode%2A> yöntemi <xref:System.Type?displayProperty=nameWithType> sınıfı. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` Veri türü olan bir başvuru türü. Ancak, Visual Basic değerlendirir bir `Object` değişken olarak bir değer türü veri başvurduğunda bir değer türü.  
  
## <a name="storage"></a>Depolama  
 Hangi veri türü başvurduğu için bir `Object` değişkeni değiştiremeyeceğinize, ancak bunun yerine bir işaretçi değerine veri değeri içermiyor. Her zaman bilgisayar belleğinde dört bayt kullanır, ancak bu değişkenin değerini temsil eden veriler için depolama içermez. İşaretçi verileri bulmak için kullandığı kodu nedeniyle `Object` değişkenleri değer türleri tutarak daha açıkça belirlenmiş değişkenlere erişmek biraz daha yavaş.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Birlikte çalışabilirlik değerlendirmeleri.** Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, diğer ortamlarda işaretçi türleri, Visual Basic ile uyumlu olmadığını aklınızda bulundurun `Object` türü.  
  
-   **Performans.** Bir değişken bildirmek ile `Object` türü olan herhangi bir nesneye bir başvuru içermesi için yeterince esnektir. Ancak, bir metot veya özellik bu tür bir değişken üzerinde çağırdığınızda, her zaman ücretler *geç bağlama* (çalışma zamanında). Zorlamak için *erken bağlama* (derleme zamanında) ve daha iyi performans, belirli bir sınıf adı ile bir değişken bildirmek veya belirli bir veri türüne.  
  
     Örneğin, belirli bir sınıf türü kullanmak bir nesne değişkeni bildirdiğinizde deneyin <xref:System.OperatingSystem>, genelleştirilmiş yerine `Object` türü. Kullanılabilir gibi en belirgin sınıfı de kullanmalısınız <xref:System.Windows.Forms.TextBox> yerine <xref:System.Windows.Forms.Control>, böylece özelliklerine ve yöntemlerine erişebilirsiniz. Genellikle kullanabileceğiniz **sınıfları** listesinde **Nesne Tarayıcısı** kullanılabilir sınıf adlarını bulmak için.  
  
-   **Genişletme.** Tüm veri türleri ve tüm başvuru türleri için genişletmek `Object` veri türü. Yani tüm türüne dönüştürebilir `Object` karşılaşmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
     Ancak, değer türleri arasında dönüştürürseniz ve `Object`, Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma*, daha yavaş yürütme olun.  
  
-   **Tür karakterleri.** `Object` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Object?displayProperty=nameWithType> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir `Object` işaret eden bir nesne örneğine değişkeni.  
  
```  
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
- [Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Nasıl yapılır: İki nesnenin aynı olup olmadığını belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
