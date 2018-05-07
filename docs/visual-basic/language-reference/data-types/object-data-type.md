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
ms.openlocfilehash: e9b1da5a88c12e0d883c3afe63be98c3fa3e9173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-data-type"></a>Nesne Veri Türü
Nesnelere atıfta adresleri tutar. Herhangi bir başvuru türü (dize, dizi, sınıf veya arabirim) atayabileceğiniz bir `Object` değişkeni. Bir `Object` değişkeni ayrıca herhangi bir değer türde veri bakın (sayısal, `Boolean`, `Char`, `Date`, yapı veya sabit listesi).  
  
## <a name="remarks"></a>Açıklamalar  
 `Object` Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere, herhangi bir veri türü veri noktası. Kullanım `Object` derleme zamanında bilmiyorsanız değişkeni hangi veri türü işaret.  
  
 Varsayılan değer olan `Object` olan `Nothing` (bir null başvuru).  
  
## <a name="data-types"></a>Veri Türleri  
 Bir değişken, sabit veya herhangi bir veri türü için bir ifade atayabilirsiniz bir `Object` değişkeni. Veri türü belirlemek için bir `Object` değişkeni şu anda başvurduğu, kullanabileceğiniz <xref:System.Type.GetTypeCode%2A> yöntemi <xref:System.Type?displayProperty=nameWithType> sınıfı. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` Veri türü olan bir başvuru türü. Ancak, Visual Basic değerlendirir bir `Object` değişken olarak bir değer türü veri başvurduğunda bir değer türü.  
  
## <a name="storage"></a>Depolama  
 Başvurduğu için hangi veri türü bir `Object` değişkeni kendisini ancak bunun yerine bir işaretçi değeri için veri değeri içermiyor. Her zaman bilgisayar belleğinde dört bayt kullanır, ancak bu değişkenin değerini temsil eden veri depolama içermez. İşaretçinin verileri bulmak için kullandığı kodu nedeniyle `Object` değer türleri bulunduran değişkenleri daha açık olarak belirtilmiş değişkenleri erişmek biraz daha yavaş.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, diğer ortamlarda işaretçi türleri Visual Basic ile uyumlu olmayan göz önünde bulundurmanız `Object` türü.  
  
-   **Performans.** Bir değişken bildirme ile `Object` türüdür herhangi bir nesneye başvuru içeren için yeterince esnektir. Ancak, bir yöntemi veya özelliği gibi bir değişken çağırdığınızda, her zaman tabi *geç bağlama* (çalışma zamanında). Zorlamak için *erken bağlama* (derleme zamanında) ve daha iyi performans, belirli bir sınıf ada sahip bir değişken bildirme veya belirli veri türüne dönüştürün.  
  
     Bir nesne değişkeni bildirme, belirli bir sınıf türü, örneğin kullanmaya çalıştığınızda <xref:System.OperatingSystem>, genelleştirilmiş yerine `Object` türü. Ayrıca gibi kullanılabilir en belirgin sınıfını kullanmalısınız <xref:System.Windows.Forms.TextBox> yerine <xref:System.Windows.Forms.Control>, böylece özelliklerini ve yöntemlerini erişebilir. Genellikle kullanabilirsiniz **sınıfları** listesinde **Nesne Tarayıcısı** kullanılabilir sınıf adlarını bulmak için.  
  
-   **Genişletme.** Tüm veri türleri ve tüm başvuru türleri için genişletmek `Object` veri türü. Bu dönüştürme için herhangi bir türü anlamına gelir `Object` karşılaşmadan olmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.  
  
     Ancak, değer türleri arasında dönüştürürseniz ve `Object`, Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma*, yürütme yavaş olun.  
  
-   **Karakterleri yazın.** `Object` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri içeriyor.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek gösterilmektedir bir `Object` işaret eden bir nesne örneğine değişkeni.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Object>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
