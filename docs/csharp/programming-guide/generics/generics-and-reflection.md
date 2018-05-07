---
title: Genel Türler ve Yansıma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 7e35c7d6712323bd7088ad68160da05cdf3a5115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generics-and-reflection-c-programming-guide"></a>Genel Türler ve Yansıma (C# Programlama Kılavuzu)
Ortak dil çalışma zamanı (CLR) çalışma zamanında genel tür bilgilere erişimi olduğundan, genel olmayan türleri için olduğu gibi aynı şekilde genel türler hakkında bilgi edinmek için yansıma kullanabilirsiniz. Daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 İçinde [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] birkaç yeni üyeler için eklenir <xref:System.Type> genel türleri için çalışma zamanı bilgileri etkinleştirmek için sınıf. Bu yöntemleri ve özellikleri nasıl kullanılacağı hakkında daha fazla bilgi için bu sınıfları belgelerine bakın. <xref:System.Reflection.Emit> Ad alanı, genel türler destekleyen yeni üyeler de içerir. Bkz: [nasıl yapılır: yansıma ile genel tür tanımlama yayma](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Genel yansıma kullanılan terimler için değişmez koşullar listesi için bkz: <xref:System.Type.IsGenericType%2A> özelliği açıklamalar.  
  
|System.Type üye adı|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Genel bir tür ise true döndürür.|  
|<xref:System.Type.GetGenericArguments%2A>|Bir dizi döndürür `Type` tür bağımsız değişkenleri temsil eden nesneler genel tür tanımında parametrelerinin yapılandırılmış bir tür veya tür için sağlanan.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Geçerli yapılandırılmış türü için temel alınan genel tür tanımı döndürür.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Bir dizi döndürür `Type` geçerli genel kısıtlamalar temsil eden nesneler parametre yazın.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Tür parametreleri için değil belirli türleri sağlanmadı türü veya kendi kapsayan türleri veya yöntemlerden herhangi birini içeriyorsa, true döndürür.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Bir birleşimini alır `GenericParameterAttributes` geçerli genel özel kısıtlamaları açıklayan bayrakları parametre yazın.|  
|<xref:System.Type.GenericParameterPosition%2A>|İçin bir `Type` temsil eden bir tür parametresi nesnesi tür parametresi konumunu genel tür tanımında veya tür parametresi bildirilen genel yöntem tanımını türü parametre listesinde alır.|  
|<xref:System.Type.IsGenericParameter%2A>|Gösteren bir değer alır olup olmadığını geçerli `Type` genel türü veya yöntemi tanımının türü parametresini temsil eder.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Gösteren bir değer alır olup olmadığını geçerli <xref:System.Type> içinden diğer oluşturulan genel türler bir genel tür tanımını temsil eder. Genel bir tür tanımı türü temsil ediyorsa true döndürür.|  
|<xref:System.Type.DeclaringMethod%2A>|Geçerli genel tanımlanan genel yöntem tür parametresi ya da genel bir yöntemle tür parametresi tanımlı değil yoksa null değerini döndürür.|  
|<xref:System.Type.MakeGenericType%2A>|Tür parametreleri için geçerli genel tür tanımı türleri dizisi öğelerini değiştirir ve döndürür bir <xref:System.Type> oluşturulan türü elde edilen temsil eden nesne.|  
  
 Ayrıca, üyeleri <xref:System.Reflection.MethodInfo> sınıfı çalışma zamanı bilgileri genel yöntemler için etkinleştir. Bkz: <xref:System.Reflection.MethodBase.IsGenericMethod%2A> özelliği açıklamalar üzerinde genel yöntemler yansıtmak için kullanılan terimler için değişmez koşullar listesi.  
  
|System.Reflection.MemberInfo üye adı|Açıklama|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Bir yöntem genel ise true, aksi durumda değeri döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Oluşturulan genel yönteminin tür bağımsız değişkenleri veya genel yöntem tanımını tür parametrelerini temsil eden tür nesneleri içeren bir dizi döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Geçerli yapılandırılmış yöntemi için temel alınan genel yöntem tanımını döndürür.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Kendisi için değil belirli türleri sağlanmadı herhangi bir tür parametre yöntemi veya kapsayan türlerinden herhangi birini içeriyorsa, true döndürür.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Varsa true değerini döndürür geçerli <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil eder.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Tür parametreleri için geçerli genel yöntem tanımını türleri dizisi öğeleri değiştirir ve döndürür bir <xref:System.Reflection.MethodInfo> oluşturulan yöntemi elde edilen temsil eden nesne.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)  
 [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Genel Türler](~/docs/standard/generics/index.md)
