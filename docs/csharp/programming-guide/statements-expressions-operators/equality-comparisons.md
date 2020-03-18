---
title: Eşitlik Karşılaştırmaları - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: f09d9891f79eda44c428d5509e341a54ad3a3eee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157110"
---
# <a name="equality-comparisons-c-programming-guide"></a>Eşitlik karşılaştırmaları (C# Programlama Kılavuzu)

Bazen eşitlik için iki değeri karşılaştırmak gerekir. Bazı durumlarda, *eşdeğerlik*olarak da bilinen *değer eşitliğini*sınarsınız, bu da iki değişkenin içerdiği değerlerin eşit olduğu anlamına gelir. Diğer durumlarda, iki değişkenin bellekte aynı temel nesneye başvurup başvurmadığını belirlemeniz gerekir. Bu tür bir eşitlik *referans eşitliği*veya *kimlik*olarak adlandırılır. Bu konu, bu iki tür eşitliği açıklar ve daha fazla bilgi için diğer konulara bağlantılar sağlar.  
  
## <a name="reference-equality"></a>Referans eşitliği

 Başvuru eşitliği, iki nesne başvurusu aynı temel nesneye başvurmak anlamına gelir. Bu, aşağıdaki örnekte gösterildiği gibi basit atama yoluyla oluşabilir.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 Bu kodda, iki nesne oluşturulur, ancak atama deyiminden sonra, her iki başvuru da aynı nesneye başvurur. Bu nedenle referans eşitliği var. İki <xref:System.Object.ReferenceEquals%2A> başvurunun aynı nesneye başvurup başvurmadığını belirlemek için yöntemi kullanın.  
  
Referans eşitliği kavramı yalnızca başvuru türleri için geçerlidir. Değer türü nesneleri, bir değer türü örneği bir değişkene atandığında, değerin bir kopyası yapıldığından, başvuru eşitliğine sahip olamaz. Bu nedenle, bellekte aynı konuma başvuran iki kutusuz yapınız asla olamaz. Ayrıca, iki değer <xref:System.Object.ReferenceEquals%2A> türünü karşılaştırmak için kullanırsanız, `false`nesnelerde bulunan değerlerin tümü aynı olsa bile, sonuç her zaman olacaktır. Bunun nedeni, her değişkenin ayrı bir nesne örneğine kutulanmış olmasıdır. Daha fazla bilgi [için bkz.](./how-to-test-for-reference-equality-identity.md)

## <a name="value-equality"></a>Değer eşitliği

 Değer eşitliği, iki nesnenin aynı değer veya değerleri içerdiği anlamına gelir. [Int](../../language-reference/builtin-types/integral-numeric-types.md) veya [bool](../../language-reference/builtin-types/bool.md)gibi ilkel değer türleri için değer eşitliği testleri basittir. Aşağıdaki örnekte [==](../../language-reference/operators/equality-operators.md#equality-operator-) gösterildiği gibi işleci kullanabilirsiniz.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 Diğer türlerin çoğunda, değer eşitliği için sınama daha karmaşıktır, çünkü türün onu nasıl tanımladığını anlamanızı gerektirir. Birden çok alanı veya özelliği olan sınıflar ve structs için değer eşitliği genellikle tüm alanların veya özelliklerin aynı değere sahip olduğu anlamına gelecek şekilde tanımlanır. Örneğin, pointA.X pointB.X'e eşitse iki `Point` nesne eşdeğer olarak tanımlanabilir ve pointA.Y pointB.Y'ye eşittir.  
  
Ancak, eşdeğerlik bir türdeki tüm alanları temel alma zorunluluğu yoktur. Bir alt kümeye dayalı olabilir. Sahip olmadığınız türleri karşılaştırdığınızda, bu tür için eşdeğerliğin nasıl tanımlandığını özellikle anladığınızdan emin olmalısınız. Kendi sınıflarınızda ve yapınızda değer eşitliğini nasıl tanımlayabilirsiniz hakkında daha fazla bilgi [için, bir tür için değer eşitliğini nasıl tanımları izle](./how-to-define-value-equality-for-a-type.md)
  
### <a name="value-equality-for-floating-point-values"></a>Kayan nokta değerleri için değer eşitliği

 Kayan nokta değerlerinin eşitlik karşılaştırmaları[(çift](../../language-reference/builtin-types/floating-point-numeric-types.md) ve [float)](../../language-reference/builtin-types/floating-point-numeric-types.md)ikili bilgisayarlarda kayan nokta aritmetik belirsizlik nedeniyle sorunludur. Daha fazla bilgi için, konuyla <xref:System.Double?displayProperty=nameWithType>ilgili açıklamalara bakın.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Referans eşitliği (Kimlik) için nasıl test yapılır?](./how-to-test-for-reference-equality-identity.md)|İki değişkenin referans eşitliği olup olmadığını nasıl belirleyeceklerini açıklar.|  
|[Tür için değer eşitliği tanımlama](./how-to-define-value-equality-for-a-type.md)|Bir tür için değer eşitliğinin özel bir tanımının nasıl sağlanır.|  
|[C# Programlama Kılavuzu](../index.md)|.NET Framework aracılığıyla C# için kullanılabilen önemli C# dil özellikleri ve özellikleri hakkında ayrıntılı bilgilere bağlantılar sağlar.|  
|[Türler](../types/index.md)|C# türü sistemi hakkında bilgi ve ek bilgilere bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
