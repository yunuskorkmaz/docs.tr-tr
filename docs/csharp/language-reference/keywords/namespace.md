---
title: "namespace (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a>namespace (C# Başvurusu)
`namespace` Anahtar sözcük, ilgili nesne kümesi içeren kapsamı bildirmek için kullanılır. Kod öğelerini düzenlemek ve genel benzersiz türleri oluşturmak için bir ad alanı kullanabilirsiniz.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanı içinde bir veya daha fazla türlerinden birini bildirebilir:  
  
-   başka bir ad alanı  
  
-   [sınıfı](../../../csharp/language-reference/keywords/class.md)  
  
-   [arabirimi](../../../csharp/language-reference/keywords/interface.md)  
  
-   [yapısı](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [temsilci seçme](../../../csharp/language-reference/keywords/delegate.md)  
  
 C# kaynak dosyasında bir ad alanını açıkça bildirme olup olmadığına, bir varsayılan ad alanı derleyici ekler. Bazen genel ad alanı da adlandırılır bu adlandırılmamış ad alanı, her dosyasında bulunur. Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanını kullanmak için kullanılabilir.  
  
 Ad alanları örtük olarak genel erişimi vardır ve bu değiştirilebilir değil. Erişim değiştiricileri öğelere bir ad atamak için bkz [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Ad alanı iki veya daha fazla bildirimlerinde tanımlamak mümkündür. Örneğin, aşağıdaki örnekte bir parçası olarak iki sınıf tanımlar `MyCompany` ad alanı:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iç içe geçmiş bir ad alanında bir statik yöntem çağrısı gösterilmektedir.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Daha Fazla Bilgi İçin  
 Ad alanlarını kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Ad alanları](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Ad alanlarını kullanma](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Namespace anahtar sözcükler](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [kullanma](../../../csharp/language-reference/keywords/using.md)
