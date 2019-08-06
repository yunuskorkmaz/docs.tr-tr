---
title: 'Nasıl yapılır: Genel ad alanı diğer ad C# programlama kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796282"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)
- [:: İşleç](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [extern](../../../csharp/language-reference/keywords/extern.md)
