---
title: 'Nasıl Yapılır: Genel - Namespace diğer kullanın C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 19d8d20ae630573b44399f8f5c5351f02b9fb1df
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236615"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Nasıl Yapılır: Genel Namespace diğer adlarını kullanma (C# Programlama Kılavuzu)
Genel bir üyeye erişme olanağı [ad alanı](../../../csharp/language-reference/keywords/namespace.md) üye aynı ada sahip başka bir varlık tarafından gizlenmiş olabilir durumlarda faydalıdır.  
  
 Örneğin, aşağıdaki kodda, `Console` çözümler `TestApp.Console` çok yerine `Console` yazın <xref:System> ad alanı.  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Kullanarak `System.Console` olduğundan hata sonuçları hala `System` ad alanı, sınıf tarafından gizlenir `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 Kullanarak bu hatayı çözmek ancak çalışabilirsiniz `global::System.Console`, şöyle:  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Sol tanımlayıcısı olduğunda `global`, aramayı sağ tanımlayıcısı için genel ad alanında başlatır. Örneğin, aşağıdaki bildirimi başvuruyor `TestApp` genel alanının bir üyesi olarak.  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Kuşkusuz, kendi ad alanları oluşturma adlı `System` önerilmez ve herhangi bir kod da gerçekleştiği karşılaşırsınız düşüktür. Ancak, daha büyük projelerinde, bir form veya başka bir ad alanı çoğaltma oluşabilir olasılığı yüksektir olur. Bu durumda, genel ad alanı niteleyicisi kök ad belirtebilirsiniz, bir garanti sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, ad alanı `System` sınıfı eklemek için kullanılan `TestClass` bu nedenle, `global::System.Console` kullanılmalıdır başvurusuna `System.Console` tarafından gizlenmiş sınıfı `System` ad alanı. Ayrıca, diğer `colAlias` ad alanına başvurmak için kullanılan `System.Collections`; bu nedenle, örneği bir <xref:System.Collections.Hashtable?displayProperty=nameWithType> ad alanı yerine bu diğer adı kullanılarak oluşturuldu.  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
**1**
**B 2**
**3 C**

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)  
- [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md)  
- [:: İşleç](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [extern](../../../csharp/language-reference/keywords/extern.md)
