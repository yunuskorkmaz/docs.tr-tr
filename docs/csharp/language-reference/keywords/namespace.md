---
title: namespace (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245622"
---
# <a name="namespace-c-reference"></a>namespace (C# Başvurusu)
`namespace` Anahtar sözcüğü, bir dizi ilgili nesneleri içeren bir kapsamı bildirmek için kullanılır. Kod öğelerini düzenlemek ve genel olarak benzersiz türleri oluşturmak için bir ad kullanabilirsiniz.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanı içinde bir veya daha fazla türlerinden birini bildirebilirsiniz:  
  
-   başka bir ad alanı  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 Açıkça bir C# kaynak dosyası içinde bir ad alanı bildirimini olsun veya olmasın, derleyici varsayılan bir ad alanı ekler. Bazen genel ad alanı adlandırılır, bu adlandırılmamış ad, her bir dosyanın yok. Genel ad alanındaki herhangi bir tanımlayıcı adlandırılmış bir ad alanında kullanılabilir.  
  
 Ad alanları, örtük olarak genel erişimi vardır ve bu değiştirilebilir değildir. Bir ad alanındaki öğeler atayabilirsiniz erişim değiştiricileri ile ilgili tartışma için bkz: [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 İki veya daha fazla bildirimlerinde ad alanı tanımlamak mümkündür. Örneğin, aşağıdaki örnekte iki sınıf kapsamında tanımlar `MyCompany` ad alanı:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir iç içe geçmiş ad alanındaki statik bir yöntemi çağırmak nasıl gösterir.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Daha Fazla Bilgi İçin  
 Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Ad Alanları](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Ad Alanlarını Kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using](../../../csharp/language-reference/keywords/using.md)
