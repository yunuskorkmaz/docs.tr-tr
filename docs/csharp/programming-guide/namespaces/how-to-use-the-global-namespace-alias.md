---
title: 'Nasıl yapılır: Genel ad alanı diğer ad C# programlama kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629448"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Nasıl yapılır: Genel ad alanı diğer adını kullanınC# (Programlama Kılavuzu)
Genel [ad](../../../csharp/language-reference/keywords/namespace.md) alanındaki bir üyeye erişme özelliği, üyenin aynı ada sahip başka bir varlık tarafından gizlenmesi durumunda faydalıdır.  
  
 Örneğin, aşağıdaki `Console` kodda, <xref:System> ad alanındaki `Console` türü yerine öğesine `TestApp.Console` çözümlenir.  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 Ad `System.Console` alanı sınıf `System` tarafından`TestApp.System`gizlendiğinden, hâlâ bir hata ile sonuçlanır:  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 Bununla birlikte, aşağıdaki gibi kullanarak `global::System.Console`bu hatayı geçici olarak çözebilirsiniz:  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 Sol tanımlayıcı `global`olduğunda, doğru tanımlayıcı için arama genel ad alanında başlar. Örneğin, aşağıdaki bildirim genel alanın bir üyesi `TestApp` olarak başvuru yapılır.  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 Kuşkusuz, adlı `System` kendi ad alanlarınızı oluşturmanız önerilmez ve bunun gerçekleştiği bir kodla karşılaşmanız düşüktür. Ancak, daha büyük projelerde ad alanı çoğaltmasının tek bir formda veya başka bir biçimde gerçekleşebileceğini çok gerçek bir olasılık. Bu durumlarda, genel ad alanı niteleyicisi, kök ad alanını belirleyebilmenizi güvence altına alabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, ad alanı `System` sınıfı `TestClass` eklemek için kullanılır, bu nedenle, `global::System.Console` `System` ad alanı tarafından gizlenen `System.Console` sınıfa başvurmak için kullanılmalıdır. Ayrıca, diğer `colAlias` ad ad alanına `System.Collections`başvurmak için kullanılır; bu nedenle <xref:System.Collections.Hashtable?displayProperty=nameWithType> , öğesinin örneği ad alanı yerine bu diğer ad kullanılarak oluşturulmuştur.  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
**A 1**
**B 2**
**C 3**

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)
- [:: İşleç](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
