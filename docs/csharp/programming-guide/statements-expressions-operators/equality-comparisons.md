---
title: Eşitlik karşılaştırmaları- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: a6876cb98a8c1b1e58e61eb650416d412467ae3d
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552416"
---
# <a name="equality-comparisons-c-programming-guide"></a>Eşitlik karşılaştırmaları (C# Programlama Kılavuzu)

Her zaman eşitlik için iki değeri karşılaştırmak gereklidir. Bazı durumlarda *denklik*olarak da bilinen *değer eşitlik*için test edersiniz, bu da iki değişken tarafından içerilen değerlerin eşit olduğu anlamına gelir. Diğer durumlarda, iki değişkenin bellekteki aynı temel nesneye başvurmadığını belirlemelisiniz. Bu tür bir eşitlik, *başvuru eşitlik*veya *kimlik*olarak adlandırılır. Bu konu, bu iki tür eşitliği açıklar ve daha fazla bilgi için diğer konulara bağlantılar sağlar.  
  
## <a name="reference-equality"></a>Başvuru eşitliği

 Başvuru eşitliği, iki nesne başvurusunun aynı temel nesneye başvurduğu anlamına gelir. Bu durum, aşağıdaki örnekte gösterildiği gibi basit atama aracılığıyla gerçekleşebilir.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 Bu kodda, iki nesne oluşturulur, ancak atama ifadesinden sonra, her iki başvuru da aynı nesneye başvurur. Bu nedenle, başvuru eşitliği vardır. İki başvuruyu aynı nesneye başvurmadığını öğrenmek için <xref:System.Object.ReferenceEquals%2A> yöntemini kullanın.  
  
 Başvuru eşitliği kavramı yalnızca başvuru türleri için geçerlidir. Değer türünün bir örneği bir değişkene atandığında, değerin bir kopyası yapıldığında değer türü nesnelerinin başvuru eşitliği olamaz. Bu nedenle, bellekte aynı konuma başvuran iki kutulanmış yapı olamaz. Ayrıca, iki değer türünü karşılaştırmak için <xref:System.Object.ReferenceEquals%2A> kullanırsanız, nesnelerde yer alan değerler aynı olsa bile sonuç her zaman `false`olur. Bunun nedeni, her değişkenin ayrı bir nesne örneğinde paketlenme örneğidir. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru eşitliği testi (kimlik)](./how-to-test-for-reference-equality-identity.md).  

## <a name="value-equality"></a>Değer eşitlik

 Değer eşitliği iki nesnenin aynı değer veya değerleri içerdiği anlamına gelir. [İnt](../../language-reference/builtin-types/integral-numeric-types.md) veya [bool](../../language-reference/builtin-types/bool.md)gibi temel değer türleri için, değer eşitlik için testler basittir. Aşağıdaki örnekte gösterildiği gibi [==](../../language-reference/operators/equality-operators.md#equality-operator-) işlecini kullanabilirsiniz.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Çoğu diğer tür için, değer eşitlik testi, türün onu nasıl tanımladığını anladığından emin olmanızı gerektirdiğinden daha karmaşıktır. Birden çok alanı veya özelliği olan sınıflar ve yapılar için, değer eşitlik genellikle tüm alanların veya özelliklerin aynı değere sahip olduğu anlamına gelir. Örneğin, pointA. X, pointB. X ve pointA. Y ' ye eşitse, iki `Point` nesne eşdeğer olacak şekilde tanımlanabilir. y öğesine eşittir.  
  
 Ancak, bir tür içindeki tüm alanları temel alan denklik gereksinimi yoktur. Bir alt kümeyi temel alabilir. Sahip olmadığınız türleri karşılaştırdığınızda, bu tür için denkliğin nasıl tanımlandığını anladığınızdan emin olmalısınız. Kendi sınıflarınızda ve yapılarda değer eşitliğini tanımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: tür Için değer eşitliği tanımlama](./how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Kayan nokta değerleri için değer eşitliği

 Kayan nokta değerlerinin ([Double](../../language-reference/builtin-types/floating-point-numeric-types.md) ve [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) eşitlik karşılaştırmaları, ikili bilgisayarlarda kayan nokta aritmetiği noktasında kesinlik eksikliği nedeniyle sorunlu bir sorunlardır. Daha fazla bilgi için <xref:System.Double?displayProperty=nameWithType>konusunun açıklamalara bakın.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik)](./how-to-test-for-reference-equality-identity.md)|İki değişkenin başvuru eşitlik içerip içermediğini nasıl belirleyebileceğinizi açıklar.|  
|[Nasıl yapılır: Tür için Değer Eşitliği Tanımlama](./how-to-define-value-equality-for-a-type.md)|Bir tür için bir özel değer eşitlik tanımı sağlamayı açıklar.|  
|[C# Programlama Kılavuzu](../index.md)|.NET Framework C# C# aracılığıyla kullanılabilecek önemli dil özellikleri ve özellikleri hakkında ayrıntılı bilgi için bağlantılar sağlar.|  
|[Türler](../types/index.md)|C# Tür sistemi ve ek bilgilerin bağlantıları hakkında bilgi sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
