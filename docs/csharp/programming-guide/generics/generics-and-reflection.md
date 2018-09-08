---
title: Genel Türler ve Yansıma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 9bbf08161162c2d0776a066098e40b57a415da6d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187143"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Genel Türler ve Yansıma (C# Programlama Kılavuzu)
Ortak dil çalışma zamanı (CLR) çalışma zamanında genel tür bilgilere erişimi olduğundan, genel olmayan türleri olduğu gibi genel türler hakkında bilgi edinmek için yansıma kullanabilirsiniz. Daha fazla bilgi için [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 İçinde [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] birkaç yeni üyeler için eklenen <xref:System.Type> genel türler için çalışma zamanı bilgilerini etkinleştirmek için sınıf. Bu sınıflarda bu yöntemlerini ve özelliklerini kullanma hakkında daha fazla bilgi için belgelere bakın. <xref:System.Reflection.Emit> Ad alanı, genel türler destekleyen yeni üyeleri de içerir. Bkz: [nasıl yapılır: yansıma ile genel tür tanımlama yayma](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Genel yansımada kullanılan terimlere ilişkin sabit koşulların listesi için bkz. <xref:System.Type.IsGenericType%2A> özelliği açıklamalar.  
  
|System.Type üye adı|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Bir tür genel ise true döndürür.|  
|<xref:System.Type.GetGenericArguments%2A>|Bir dizi döndürür `Type` tür bağımsız değişkenlerini temsil eden nesneleri, genel tür tanımı parametreleri oluşturulmuş bir türü veya tür için sağlanan.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Geçerli oluşturulan tür temel genel tür tanımını döndürür.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Bir dizi döndürür `Type` tür parametresinin geçerli genel kısıtlamalar temsil eden nesneleri.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Türü veya herhangi bir kapsayan tür veya yöntemin kendisi için değil özel türleri sağlanmadı tür parametreleri içeriyorsa true döndürür.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Bir birleşimi alır `GenericParameterAttributes` geçerli genel özel kısıtlamaları tanımlayan bayraklar parametresi yazın.|  
|<xref:System.Type.GenericParameterPosition%2A>|İçin bir `Type` bir tür parametresini temsil nesneyi tür parametresi genel tür tanımı veya tür parametresi bildirimi genel yöntem tanımının türü parametre listesini konumunu alır.|  
|<xref:System.Type.IsGenericParameter%2A>|Belirten bir değer alır olup olmadığını geçerli `Type` genel bir tür veya yöntem tanımının bir tür parametresini temsil eder.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Belirten bir değer alır olup olmadığını geçerli <xref:System.Type> içinden diğer oluşturulan genel türler bir genel tür tanımını temsil eder. Genel tür tanımı türü temsil ediyorsa true döndürür.|  
|<xref:System.Type.DeclaringMethod%2A>|Geçerli genel tanımlanan genel yöntemin tür parametresi veya tür parametresi, genel bir yöntem tarafından tanımlanmamış yoksa null değerini döndürür.|  
|<xref:System.Type.MakeGenericType%2A>|Geçerli genel tür tanımının türleri tür parametreleri için bir dizi öğelerinin yerini alır ve döndürür bir <xref:System.Type> oluşturulan türü ortaya çıkan temsil eden nesne.|  
  
 Ayrıca, üyeleri <xref:System.Reflection.MethodInfo> sınıfını genel metotlar için çalışma zamanı bilgilerini etkinleştirin. Bkz: <xref:System.Reflection.MethodBase.IsGenericMethod%2A> özelliği açıklamalar genel yöntemlerin yansıtmak için kullanılan terimler ilişkin sabit koşulların listesi.  
  
|System.Reflection.MemberInfo üye adı|Açıklama|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Genel bir yöntemi ise true döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Tür bağımsız değişkenlerini oluşturulmuş bir genel yöntem veya bir genel yöntem tanımının Tür parametreleri temsil eden tür nesneleri dizisi döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Geçerli yapılandırılmış yöntemi için temel alınan genel yöntem tanımını döndürür.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Yöntem veya kapsayan türlerinden birinin kendisi için değil özel türleri sağlanmadı herhangi bir tür parametreleri içeriyorsa true döndürür.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Gerekirse true döndürür geçerli <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil eder.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Geçerli genel yöntem tanımının türleri tür parametreleri için bir dizi öğelerinin yerini alır ve döndürür bir <xref:System.Reflection.MethodInfo> oluşturulmuş yöntemi ortaya çıkan temsil eden nesne.|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
- [Genel Türler](~/docs/standard/generics/index.md)
