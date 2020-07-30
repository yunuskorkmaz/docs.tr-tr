---
title: Bir tür için değer eşitliği tanımlama-C# Programlama Kılavuzu
description: Bir tür için değer eşitliği tanımlama hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: cf4449618c2b57f21855354f2250d41a403b4d57
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381651"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Bir tür için değer eşitliği tanımlama (C# Programlama Kılavuzu)

Bir sınıf veya yapı tanımladığınızda, türün tür için özel bir değer eşitlik tanımı (veya denklik) oluşturmak mantıklı olup olmadığına karar verirsiniz. Genellikle, tür nesnelerinin bir sıralama koleksiyonuna eklenmesi beklendiğinde veya birincil amaçları bir alan veya özellik kümesini depoladığınızda değer eşitliğini uygulamalısınız. Değer eşitlik tanımınızı, türdeki tüm alanların ve özelliklerin bir karşılaştırmasına dayandırıp veya tanımı bir alt küme üzerinde temel alabilirsiniz.

Her iki durumda da, hem sınıflarda hem de yapılarda, uygulamanız beş denklik garantisini izlemelidir (aşağıdaki kurallar Için, `x` `y` ve null olmadığını varsayın `z` ):  
  
1. `x.Equals(x)`döndürür `true` . Bu, yansımalı özelliği olarak adlandırılır.  
  
2. `x.Equals(y)`ile aynı değeri döndürür `y.Equals(x)` . Buna simetrik Özellik denir.  
  
3. `(x.Equals(y) && y.Equals(z))`dönerse `true` , `x.Equals(z)` döndürür `true` . Bu, geçişli özellik olarak adlandırılır.  
  
4. Art arda yapılan çağırmaları, `x.Equals(y)` x ve y tarafından başvurulan nesneler değiştirilmedikçe aynı değeri döndürür.  
  
5. Null olmayan herhangi bir değer null değerine eşit değildir. Ancak, CLR tüm yöntem çağrılarında null değerini denetler ve `NullReferenceException` başvuru null olduğunda bir oluşturur `this` . Bu nedenle, `x.Equals(y)` null olduğunda bir özel durum oluşturur `x` . Bu, bağımsız değişkenine göre 1 veya 2 olan kuralları keser `Equals` .

 Tanımladığınız herhangi bir yapı, <xref:System.ValueType?displayProperty=nameWithType> yöntemin geçersiz kılınmasına devraldığı bir değer eşitlik varsayılan uygulamasına sahiptir <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> . Bu uygulama, türündeki tüm alanları ve özellikleri incelemek için yansıma kullanır. Bu uygulama doğru sonuçlar üretse de, özellikle tür için yazdığınız özel bir uygulamayla karşılaştırıldığında nispeten yavaştır.  
  
 Değer eşitlik için uygulama ayrıntıları sınıflar ve yapılar için farklıdır. Ancak, her iki sınıf ve yapı, eşitlik uygulamak için aynı temel adımları gerektirir:  
  
1. [Sanal](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi geçersiz kılın. Çoğu durumda, uygulamanız `bool Equals( object obj )` yalnızca `Equals` arabirimin uygulanması olan türe özgü yöntemi çağırmalıdır <xref:System.IEquatable%601?displayProperty=nameWithType> . (Bkz. 2. adım.)  
  
2. <xref:System.IEquatable%601?displayProperty=nameWithType>Bir türe özgü Yöntem sağlayarak arabirimini uygulayın `Equals` . Bu, gerçek denklik karşılaştırmasının gerçekleştirildiği yerdir. Örneğin, sizin yazarken yalnızca bir veya iki alanı karşılaştırarak eşitlik tanımlamaya karar verebilirsiniz. ' Den özel durumlar atamayın `Equals` . Yalnızca sınıflar için: Bu yöntem yalnızca sınıfında belirtilen alanları incelemelidir. `base.Equals`Temel sınıfta bulunan alanları incelemek için çağırmalıdır. (Türü doğrudan öğesinden devralırsa <xref:System.Object> , ' <xref:System.Object> nin uygulanması <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> bir başvuru eşitlik denetimi gerçekleştirdiğinden, bunu kullanmayın.)  
  
3. İsteğe bağlı ancak önerilir: [==](../../language-reference/operators/equality-operators.md#equality-operator-) ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçlerini aşırı yükleme.  
  
4. <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>Değer eşitliği olan iki nesnenin aynı karma kodu üretmesi için geçersiz kılın.  
  
5. İsteğe bağlı: "büyüktür" veya "küçüktür" tanımlarını desteklemek Için, <xref:System.IComparable%601> türü için arabirimi uygulayın ve ayrıca [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) ve [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) işleçlerini aşırı yüklere ekleyebilirsiniz.  
  
 Aşağıdaki ilk örnek bir sınıf uygulamasını gösterir. İkinci örnek bir struct uygulamasını gösterir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir sınıfta (başvuru türü) nasıl değer eşitlik uygulanacağını gösterir.  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Sınıflarda (başvuru türleri), her iki yöntemin varsayılan uygulanması, bir <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> değer eşitlik denetimi değil, bir başvuru eşitlik karşılaştırması gerçekleştirir. Bir uygulayıcının sanal yöntemi geçersiz kıldığında amaç, bu değere eşitlik semantiğini vermektir.  
  
 `==`Ve `!=` işleçleri, sınıf tarafından aşırı yüklenmese bile sınıflarla birlikte kullanılabilir. Ancak, varsayılan davranış bir başvuru eşitlik denetimi gerçekleştirdir. Bir sınıfında, yöntemini aşırı yüklüyorsanız, `Equals` `==` ve `!=` işleçlerini aşırı yükletmelisiniz, ancak gerekli değildir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir yapıda değer eşitlik 'nın nasıl uygulanacağını gösterir (değer türü):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Yapılar için, varsayılan uygulamasının (sürümünde <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> geçersiz kılınan sürüm <xref:System.ValueType?displayProperty=nameWithType> ), türdeki her alanın değerlerini karşılaştırmak için yansıma kullanarak bir değer eşitlik denetimi gerçekleştirir. Bir uygulayıcının bir yapıda sanal yöntemi geçersiz kıldığında `Equals` Amaç, eşitlik denetimini gerçekleştirmeye yönelik daha verimli bir yol sağlamaktır ve isteğe bağlı olarak yapının alanının veya özelliklerinin bir alt kümesinde karşılaştırmayı temel alır.  
  
 [==](../../language-reference/operators/equality-operators.md#equality-operator-)Struct, açıkça aşırı yüklemediği müddetçe ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçleri bir struct üzerinde çalışamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik karşılaştırmaları](equality-comparisons.md)
- [C# programlama kılavuzu](../index.md)
