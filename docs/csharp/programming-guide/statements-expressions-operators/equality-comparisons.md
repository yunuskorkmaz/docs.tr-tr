---
title: Eşitlik karşılaştırmaları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 50b1cdb8b7e5087f1fd6669e7163e2c15e9b23bf
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423653"
---
# <a name="equality-comparisons-c-programming-guide"></a>Eşitlik karşılaştırmaları (C# Programlama Kılavuzu)

Bazen, eşitlik için iki değeri karşılaştırmak gereklidir. Bazı durumlarda, için test ettiğiniz *değer eşitliği*olarak da bilinen *denklik*, iki değişkenin içerdiği değerlerin eşit olduğu anlamına gelir. Diğer durumlarda iki değişkenin bellekte aynı alt nesneye başvurmadığını belirlemeniz gerekir. Bu yeni eşitlik türüne adlı *eşitlik*, veya *kimlik*. Bu konu, bu iki eşitlik türünü açıklar ve daha fazla bilgi için diğer konulara bağlantılar sağlar.  
  
## <a name="reference-equality"></a>Başvuru eşitliği

 Başvuru eşitliği iki nesne başvurusunun aynı alt nesneye başvurması anlamına gelir. Aşağıdaki örnekte gösterildiği gibi bu basit atama yoluyla oluşabilir.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 Bu kodda, iki nesne oluşturulur ancak arama deyiminden sonra her iki başvuru aynı nesneye başvurun. Bu nedenle başvuru eşitliğine sahiplerdir. Kullanım <xref:System.Object.ReferenceEquals%2A> iki başvurunun aynı nesneye başvurup başvurmadığını belirlemek için yöntemi.  
  
 Başvuru eşitliği kavramı yalnızca başvuru türleri için geçerlidir. Bir değer türü örneği bir değişkene atandığında değerin kopyası yapıldığı için değer türünde nesneler başvuru eşitliğine sahip olamaz. Bu nedenle asla bellekte aynı konuma başvuran iki kutusuz olabilir. Ayrıca, kullanırsanız <xref:System.Object.ReferenceEquals%2A> iki veri türünü karşılaştırmak için sonuç her zaman olacaktır `false`, nesnelerin içindeki değerler aynı olsa bile. Her bir değişken, bir ayrı bir nesne örneğinde Kutulu olmasıdır. Daha fazla bilgi için [nasıl yapılır: (Kimlik) başvuru eşitliği testi](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  

## <a name="value-equality"></a>Değer eşitliği

 Değer eşitliği, iki nesnenin aynı değeri veya değerleri içerdiği anlamına gelir. İlkel değer türleri gibi [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) veya [bool](../../../csharp/language-reference/keywords/bool.md), için değer eşitliği testleri kolaydır. Kullanabileceğiniz [ == ](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) işleci, aşağıdaki örnekte gösterildiği gibi.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Nasıl türün nasıl tanımladığını anlamanız gerektiğinden diğer birçok tür için değer eşitliği testi çok daha karmaşıktır. Sınıflar ve birden çok alanı veya özelliği olan yapı birimleri için değer eşitliği genellikle tüm alanların veya özelliklerin aynı değere sahip anlamına gelecek şekilde olarak tanımlanır. Örneğin, iki `Point` nesneleri, pointA.X pointB.X eşitse ve pointa.y ile pointB.Y eşitse denk olarak tanımlanabilir.  
  
 Ancak, tüm alanları bir tür denklik dayanması gereksinimi yoktur. Bir alt kümesi üzerinde temel alabilir. Sahibi olmadığınız türleri karşılaştırırken özellikle denklik bu tür için nasıl tanımlandığını anlamak emin olmanız gerekir. Kendi sınıflar ve yapı birimlerinizde değer eşitliği tanımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Kayan nokta değerleri için değer eşitliği

 Kayan nokta değerlerinin eşitlik karşılaştırmaları ([çift](../../../csharp/language-reference/keywords/double.md) ve [float](../../../csharp/language-reference/keywords/float.md)) ikili bilgisayarlarda kayan nokta aritmetiği kesinlik eksikliği nedeniyle sorunludur. Daha fazla bilgi için başlığındaki açıklamalara bakın <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: (Kimlik) başvuru eşitliği testi](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|İki değişkenin başvuru eşitliğine sahip olup olmadığını belirlemek açıklar.|  
|[Nasıl yapılır: Tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Bir tür için değer eşitliği özel bir tanımını sağlamak açıklar.|  
|[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)|Önemli C# dili özellikleri ve C# .NET Framework aracılığıyla kullanılabilen özellikleri hakkında ayrıntılı bilgi için bağlantılar sağlar.|  
|[Türler](../../../csharp/programming-guide/types/index.md)|C# türünde sistem ve ek bilgi bağlantıları hakkında bilgi sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
