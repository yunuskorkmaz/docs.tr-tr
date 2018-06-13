---
title: Eşitlik Karşılaştırmaları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: c1abee8636cf540d42d92eb7496fb078f06e6e0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335254"
---
# <a name="equality-comparisons-c-programming-guide"></a>Eşitlik Karşılaştırmaları (C# Programlama Kılavuzu)
Bazen, eşitlik için iki değerleri karşılaştırmak gereklidir. Bazı durumlarda için test ettiğiniz *değer eşitlik*, olarak da bilinen *eşdeğer*, iki değişken tarafından bulunan değerlerin eşit olup olmadığını anlamına gelir. Diğer durumlarda, iki değişken aynı nesnesini bellekte başvurmak olup olmadığını belirlemeniz gerekir. Bu tür bir eşitlik adlı *başvuru eşitliği*, veya *kimlik*. Bu konu, bu iki tür eşitlik açıklar ve daha fazla bilgi için diğer konulara bağlantılar sağlar.  
  
## <a name="reference-equality"></a>Başvuru eşitliği  
 Referans eşitlik iki nesne başvuruları aynı temel nesneye başvuran anlamına gelir. Aşağıdaki örnekte gösterildiği gibi bu basit atama oluşabilir.  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 Bu kodda, iki nesne oluşturulur, ancak atama deyimi sonra her iki başvuruları aynı nesneye başvurun. Bu nedenle başvuru eşitliği gerekir. Kullanım <xref:System.Object.ReferenceEquals%2A> iki başvuruları aynı nesneye başvuran olup olmadığını belirlemek amacıyla yöntemi.  
  
 Referans eşitlik kavramı yalnızca başvuru türleri için geçerlidir. Bir değişkene bir değer türü örneği atandığında, değerin bir kopyası oluşturulur çünkü değer türü nesneler başvuru eşitliği sahip olamaz. Bu nedenle, bellek aynı konumda başvurmak iki sarmalanmamış yapılar hiçbir zaman olabilir. Ayrıca, kullanırsanız <xref:System.Object.ReferenceEquals%2A> iki değer türleri karşılaştırmak için sonucu her zaman olacaktır `false`nesneleri bulunan değerlerin tüm aynı olsa bile. Her bir değişken ayrı bir nesne örneğine Kutulu olmasıdır. Daha fazla bilgi için bkz: [nasıl yapılır: (kimlik) başvuru eşitliği testi](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  
  
## <a name="value-equality"></a>Değer eşitliği  
 Değer eşitliği iki nesnenin aynı değeri veya değerler içeren anlamına gelir. İçin basit değer türleri gibi [int](../../../csharp/language-reference/keywords/int.md) veya [bool](../../../csharp/language-reference/keywords/bool.md), testler için değer eşitliği kolay. Kullanabileceğiniz [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) aşağıdaki örnekte gösterildiği gibi işleci.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Ne tür tanımlar anlamak gerektirdiğinden diğer çoğu türleri için değer eşitlik için test daha karmaşıktır. Sınıflar ve birden çok özellik veya alana sahip yapılar için değer eşitliği genellikle tüm alanları veya özellikleri aynı değere sahip anlamına tanımlanır. Örneğin, iki `Point` nesneleri için pointB.X pointA.X eşittir ve pointA.Y pointB.Y için eşit ise eşdeğer olarak tanımlanabilir.  
  
 Ancak, eşdeğer bir türdeki tüm alanları dayanması gereksinimi yoktur. Bir alt kümesinde dayanabilir. Sahibi olmadığınız türleri karşılaştırdığınızda, özellikle nasıl eşdeğer bu türü için tanımlı anlamak emin olmanız gerekir. Kendi sınıflar ve yapılar değer eşitliği tanımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Kayan nokta değerleri için değer eşitliği  
 Eşitlik karşılaştırmaları kayan noktası değerleri ([çift](../../../csharp/language-reference/keywords/double.md) ve [float](../../../csharp/language-reference/keywords/float.md)) imprecision noktası aritmetik ikili bilgisayarlarda kayan nedeniyle sorunludur. Açıklamalar konusunda daha fazla bilgi için bkz: <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|İki değişken başvuru eşitliği sahip olup olmadığınızı belirlemek açıklar.|  
|[Nasıl yapılır: Tür için Değer Eşitliği Tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Bir tür için değer eşitliği özel bir tanımını sağlamak üzere açıklar.|  
|[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)|Önemli C# dil özellikleri ve C# .NET çerçevesi aracılığıyla kullanılabilen özellikleri hakkında ayrıntılı bilgi için bağlantılar sağlar.|  
|[Türler](../../../csharp/programming-guide/types/index.md)|C# tür sistemi ve ek bilgilere bağlantılar hakkında bilgi sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
