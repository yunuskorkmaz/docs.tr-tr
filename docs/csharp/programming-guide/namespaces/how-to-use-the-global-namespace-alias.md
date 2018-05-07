---
title: 'Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 74f51d18ddda1ae4706b78aaf713683d2e505d2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma (C# Programlama Kılavuzu)
Genel olarak bir üyeye erişme olanağı [ad alanı](../../../csharp/language-reference/keywords/namespace.md) üye aynı ada sahip başka bir varlık tarafından gizlenebilir durumlarda faydalıdır.  
  
 Örneğin, aşağıdaki kodda, `Console` çözümler `TestApp.Console` çok yerine `Console` yazın <xref:System> ad alanı.  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 Kullanarak `System.Console` çünkü hatayla sonuçlanır hala `System` ad alanı sınıf tarafından gizli `TestApp.System`:  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 Ancak, kullanarak bu hata için geçici çözüm bulabilirsiniz `global::System.Console`, şöyle:  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Sol tanımlayıcı olduğunda `global`, arama sağ tanımlayıcısı için genel ad alanında başlatır. Örneğin, aşağıdaki bildirimi başvuran `TestApp` genel alanının bir üyesi olarak.  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Belli ki, kendi ad alanları oluşturma adlı `System` tavsiye edilmez ve bu oluşmuş herhangi bir kod karşılaşırsınız düşüktür. Ancak, daha büyük projelerde bir form veya başka bir ad alanı çoğaltma oluşabilir çok gerçek olasılığı vardır. Bu durumda, genel ad alanı niteleyicisi kök ad alanını belirtebilirsiniz, garantisi yoktur.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, ad alanı `System` sınıfı eklemek için kullanılan `TestClass` bu nedenle, `global::System.Console` kullanılmalıdır başvuru `System.Console` tarafından gizli sınıfı `System` ad alanı. Ayrıca, diğer ad `colAlias` ad alanına başvurmak için kullanılan `System.Collections`; bu nedenle, örneği bir <xref:System.Collections.Hashtable?displayProperty=nameWithType> ad alanı yerine bu diğer adı kullanılarak oluşturuldu.  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 **1**  
**B 2**  
**C 3**   
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)  
 [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md)  
 [:: İşleci](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [extern](../../../csharp/language-reference/keywords/extern.md)
