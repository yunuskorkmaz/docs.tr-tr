---
title: Bir tür C# Programlama Kılavuzu için değer eşitliği tanımlama
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 5eb1aaf96097d2c00cb04e24e65e01464f5f00c6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711980"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Bir tür için değer eşitliği tanımlama (C# Programlama Kılavuzu)

Bir sınıf veya yapı tanımladığınızda, türün tür için özel bir değer eşitlik tanımı (veya denklik) oluşturmak mantıklı olup olmadığına karar verirsiniz. Genellikle, tür nesnelerinin bir sıralama koleksiyonuna eklenmesi beklendiğinde veya birincil amaçları bir alan veya özellik kümesini depoladığınızda değer eşitliğini uygulamalısınız. Değer eşitlik tanımınızı, türdeki tüm alanların ve özelliklerin bir karşılaştırmasına dayandırıp veya tanımı bir alt küme üzerinde temel alabilirsiniz. Ancak her iki durumda da, hem sınıflarda hem de yapılarda, uygulamanız beş denklik garantisini izlemelidir:  
  
1. `x.Equals(x)` `true`döndürür. Bu, yansımalı özelliği olarak adlandırılır.  
  
2. `x.Equals(y)`, `y.Equals(x)`ile aynı değeri döndürür. Buna simetrik Özellik denir.  
  
3. `(x.Equals(y) && y.Equals(z))` `true`döndürürse `x.Equals(z)` `true`döndürür. Bu, geçişli özellik olarak adlandırılır.  
  
4. `x.Equals(y)` art arda çağırmaları, x ve y tarafından başvurulan nesneler değiştirilmedikçe aynı değeri döndürür.  
  
5. `x.Equals(null)` `false`döndürür. Ancak, `null.Equals(null)` bir özel durum oluşturur; Yukarıdaki iki kural numarasına uymaz.  
  
 Tanımladığınız herhangi bir yapı, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yönteminin <xref:System.ValueType?displayProperty=nameWithType> geçersiz kılmasına devraldığı bir değer eşitlik varsayılan uygulamasına sahiptir. Bu uygulama, türündeki tüm alanları ve özellikleri incelemek için yansıma kullanır. Bu uygulama doğru sonuçlar üretse de, özellikle tür için yazdığınız özel bir uygulamayla karşılaştırıldığında nispeten yavaştır.  
  
 Değer eşitlik için uygulama ayrıntıları sınıflar ve yapılar için farklıdır. Ancak, her iki sınıf ve yapı, eşitlik uygulamak için aynı temel adımları gerektirir:  
  
1. [Sanal](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemini geçersiz kılın. Çoğu durumda, `bool Equals( object obj )` uygulamanız yalnızca <xref:System.IEquatable%601?displayProperty=nameWithType> arabiriminin uygulanması olan türe özgü `Equals` yöntemini çağırmalıdır. (Bkz. 2. adım.)  
  
2. Türe özgü bir `Equals` yöntemi sağlayarak <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimini uygulayın. Bu, gerçek denklik karşılaştırmasının gerçekleştirildiği yerdir. Örneğin, sizin yazarken yalnızca bir veya iki alanı karşılaştırarak eşitlik tanımlamaya karar verebilirsiniz. `Equals`özel durumlar atamayın. Yalnızca sınıflar için: Bu yöntem yalnızca sınıfında belirtilen alanları incelemelidir. Temel sınıftaki alanları incelemek için `base.Equals` çağırmalıdır. (<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object> uygulanması bir başvuru eşitlik denetimi gerçekleştirdiğinden, bu tür doğrudan <xref:System.Object>devralırsa bunu kullanmayın.)  
  
3. İsteğe bağlı ancak önerilir: [==](../../language-reference/operators/equality-operators.md#equality-operator-) ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçlerini aşırı yükleme.  
  
4. Değer eşitliği olan iki nesnenin aynı karma kodu üretmesi için <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> geçersiz kılın.  
  
5. İsteğe bağlı: "büyüktür" veya "küçüktür" tanımlarını desteklemek Için, türü için <xref:System.IComparable%601> arabirimini uygulayın ve ayrıca [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) ve [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) işleçlerini aşırı yükleme yapın.  
  
 Aşağıdaki ilk örnek bir sınıf uygulamasını gösterir. İkinci örnek bir struct uygulamasını gösterir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir sınıfta (başvuru türü) nasıl değer eşitlik uygulanacağını gösterir.  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Sınıflarda (başvuru türleri), her iki <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yönteminin varsayılan uygulanması, bir değer eşitlik denetimi değil, bir başvuru eşitlik karşılaştırması gerçekleştirir. Bir uygulayıcının sanal yöntemi geçersiz kıldığında amaç, bu değere eşitlik semantiğini vermektir.  
  
 `==` ve `!=` işleçleri, sınıf tarafından aşırı yüklenmese bile sınıflarla birlikte kullanılabilir. Ancak, varsayılan davranış bir başvuru eşitlik denetimi gerçekleştirdir. Bir sınıfında, `Equals` yöntemini aşırı yüklüyorsanız `==` ve `!=` işleçlerini aşırı yükmelisiniz, ancak gerekli değildir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir yapıda değer eşitlik 'nın nasıl uygulanacağını gösterir (değer türü):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Yapılar için <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> varsayılan uygulamasıdır (<xref:System.ValueType?displayProperty=nameWithType>geçersiz kılınan sürümdür), tür içindeki her alanın değerlerini karşılaştırmak için yansıma kullanarak bir değer eşitlik denetimi gerçekleştirir. Bir uygulayıcının bir yapıda sanal `Equals` yöntemi geçersiz kıldığında amaç, değer eşitlik denetimini gerçekleştirmeye yönelik daha verimli bir yol sağlamaktır ve isteğe bağlı olarak yapının alanının veya özelliklerinin bazı alt kümesinde karşılaştırmayı temel alır.  
  
 Yapı açıkça onları aşırı yüklemediği takdirde, [==](../../language-reference/operators/equality-operators.md#equality-operator-) ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçleri bir struct üzerinde çalışamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik karşılaştırmaları](equality-comparisons.md)
- [C# Programlama Kılavuzu](../index.md)
