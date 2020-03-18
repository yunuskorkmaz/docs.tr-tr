---
title: Bir tür için değer eşitliği nasıl tanımlanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 140be18698a40be8f394b31fcd42b97d6685cb98
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157097"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Bir tür için değer eşitliği nasıl tanımlanır (C# Programlama Kılavuzu)

Bir sınıf veya yapı tanımladığınızda, tür için özel bir değer eşitliği (veya eşdeğerlik) tanımı oluşturmanın mantıklı olup olmadığına karar verirsiniz. Genellikle, türdeki nesnelerin bir tür koleksiyona eklenmesi beklendiğinde veya birincil amaçları bir alan kümesini veya özellikleri depolamak olduğunda değer eşitliği uygularsınız. Değer eşitliği tanımınızı, türdeki tüm alanların ve özelliklerin karşılaştırılmasına dayandırabilir veya tanımı bir alt kümeye dayandırabilirsiniz.

Her iki durumda da ve her iki sınıf ve yapıda, uygulamanız denklik beş garantisine uymalıdır `x` `y` (Aşağıdaki kurallar için, geçersiz olduğunu varsayalım): `z`  
  
1. `x.Equals(x)`döndürür. `true` Buna refleksif özellik denir.  
  
2. `x.Equals(y)`ile aynı değeri `y.Equals(x)`döndürür. Buna simetrik özellik denir.  
  
3. `(x.Equals(y) && y.Equals(z))` dönerse, `true`sonra `x.Equals(z)` `true`döner. Buna geçişli özellik denir.  
  
4. X ve y `x.Equals(y)` tarafından başvurulan nesneler değiştirilmediğinden, ardışık olarak aynı değeri döndürme çağrıları.  
  
5. Null olmayan herhangi bir değer null eşit değildir. Ancak, CLR tüm yöntem aramalarında null'u `NullReferenceException` denetler ve başvurunun `this` null olması durumunda bir atar. Bu `x.Equals(y)` nedenle, null `x` olduğunda bir özel durum atar. Bu, bağımsız değişkene bağlı olarak 1 `Equals`veya 2 kuralını bozar.

 Tanımladığınız herhangi bir yapı, <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemin geçersiz kılınan geçersiz kılındığı değer eşitliğinin varsayılan uygulamasına sahiptir. Bu uygulama, türdeki tüm alanları ve özellikleri incelemek için yansıma kullanır. Bu uygulama doğru sonuçlar üretse de, türü için özel olarak yazdığınız özel bir uygulamaya göre nispeten yavaştır.  
  
 Değer eşitliği için uygulama ayrıntıları sınıflar ve structs için farklıdır. Ancak, hem sınıflar hem de structs eşitliği uygulamak için aynı temel adımları gerektirir:  
  
1. [Sanal](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi geçersiz kılın. Çoğu durumda, uygulamanız `bool Equals( object obj )` sadece <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimin uygulanması `Equals` türüne özgü yöntem içine çağırmak gerekir. (Bkz. adım 2.)  
  
2. Türe <xref:System.IEquatable%601?displayProperty=nameWithType> özgü `Equals` bir yöntem sağlayarak arabirimi uygulayın. Gerçek denklik karşılaştırmasının yapıldığı yer burasıdır. Örneğin, türünüzdeki yalnızca bir veya iki alanı karşılaştırarak eşitliği tanımlamaya karar verebilirsiniz. 'den `Equals`istisnalar atmayın. Yalnızca sınıflar için: Bu yöntem yalnızca sınıfta bildirilen alanları incelemelidir. Taban sınıftaki alanları incelemek için çağrı `base.Equals` lmalıdır. (Başvuru eşitliği denetimi <xref:System.Object> <xref:System.Object> nin uygulanması <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> olduğundan, tür doğrudan devralıyorsa bunu yapmayın.)  
  
3. İsteğe bağlı ama [==](../../language-reference/operators/equality-operators.md#equality-operator-) önerilen: Aşırı yük ve [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) operatörleri.  
  
4. Değer <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> eşitliği olan iki nesnenin aynı karma kodu oluşturması için geçersiz kılın.  
  
5. İsteğe bağlı: "Büyük" veya "daha az" <xref:System.IComparable%601> tanımlarını desteklemek için, türünüz [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) için arabirimi uygulayın ve ayrıca ve işleçleri aşırı yükleyin.  
  
 Aşağıdaki ilk örnek bir sınıf uygulamasını gösterir. İkinci örnek, bir yapı uygulamasını gösterir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir sınıfta (başvuru türü) değer eşitliğinin nasıl uygulanacağını gösterir.  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Sınıflarda (başvuru türleri) her <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> iki yöntemin varsayılan uygulaması, değer eşitliği denetimi değil, bir başvuru eşitliği karşılaştırması gerçekleştirir. Bir uygulayıcı sanal yöntemi geçersiz kılarsa, amaç ona değer eşitliği semantik vermektir.  
  
 Ve `==` `!=` işleçler, sınıf aşırı yüklemese bile sınıflarla birlikte kullanılabilir. Ancak, varsayılan davranış bir başvuru eşitliği denetimi gerçekleştirmektir. Bir sınıfta, `Equals` yöntemi aşırı yüklerseniz, ve `==` `!=` işleçleri aşırı yüklemeniz gerekir, ancak gerekli değildir.  

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir yapıda (değer türünde) değer eşitliğinin nasıl uygulanacağını gösterir:  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Structs için, varsayılan <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> uygulama (içinde <xref:System.ValueType?displayProperty=nameWithType>geçersiz sürümü olan) türünde her alanın değerlerini karşılaştırmak için yansıma kullanarak bir değer eşitliği denetimi gerçekleştirir. Bir uygulayıcı bir yapıdaki `Equals` sanal yöntemi geçersiz kılarken, amaç değer eşitliği denetimini gerçekleştirmek için daha verimli bir araç sağlamak ve isteğe bağlı olarak karşılaştırmayı yapı alanının veya özelliklerinin bazı alt kümesine dayandırmaktır.  
  
 ve [==](../../language-reference/operators/equality-operators.md#equality-operator-) [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçleri, yapı açıkça aşırı yüklemedikçe bir yapı üzerinde çalışamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik karşılaştırmaları](equality-comparisons.md)
- [C# programlama kılavuzu](../index.md)
