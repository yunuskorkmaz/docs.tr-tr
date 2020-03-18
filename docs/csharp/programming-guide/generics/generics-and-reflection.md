---
title: Jenerik ve Yansıma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 4893bf5ebe73988bb6535cc2a85591ff0dde6ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712175"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Genel Türler ve Yansıma (C# Programlama Kılavuzu)
Ortak Dil Çalışma Zamanı (CLR) çalışma zamanında genel tür bilgilerine erişebildiği için, genel olmayan türler hakkında olduğu gibi genel türler hakkında bilgi edinmek için yansımayı kullanabilirsiniz. Daha fazla bilgi için [Çalışma Süresi'ndeki Genel Bilgiler'e](./generics-in-the-run-time.md)bakın.  
  
 .NET Framework 2.0'da, genel türler <xref:System.Type> için çalışma zamanı bilgilerini etkinleştirmek için sınıfa birkaç yeni üye eklenir. Bu yöntemlerin ve özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bu sınıflardaki belgelere bakın. Ad <xref:System.Reflection.Emit> alanı, genel leri destekleyen yeni üyeler de içerir. [Bkz. Nasıl: Yansıma Yayı ile Genel Bir Tür Tanımlayın.](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)  
  
 Genel yansımada kullanılan terimleriçin değişmez koşulların listesi <xref:System.Type.IsGenericType%2A> için özellik açıklamalarına bakın.  
  
|System.Type Üye Adı|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Bir tür genelse doğru döndürür.|  
|<xref:System.Type.GetGenericArguments%2A>|Yapılandırılan bir `Type` tür için sağlanan tür bağımsız değişkenlerini veya genel bir tür tanımının tür parametrelerini temsil eden bir nesne dizisi döndürür.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Geçerli yapılandırılan tür için temel genel tür tanımını verir.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Geçerli genel `Type` tür parametresindeki kısıtlamaları temsil eden bir nesne dizisi verir.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Tür veya çevreleyen tür veya yöntemleri, belirli türler için sağverilmiş olmayan tür parametreleri içeriyorsa doğru döndürür.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Geçerli genel `GenericParameterAttributes` tür parametresinin özel kısıtlamalarını açıklayan bayrakların bir birleşimini alır.|  
|<xref:System.Type.GenericParameterPosition%2A>|Bir `Type` tür parametresini temsil eden bir nesne için, tür parametresini bildiren genel tür tanımı veya genel yöntem tanımının tür parametre listesindeki tür parametresinin konumunu alır.|  
|<xref:System.Type.IsGenericParameter%2A>|Geçerlinin `Type` genel bir tür veya yöntem tanımının tür parametresini temsil edip etmediğini gösteren bir değer alır.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Geçerlinin, <xref:System.Type> diğer genel türlerin oluşturulabileceği genel bir tür tanımını temsil edip etmediğini belirten bir değer alır. Tür, genel bir türün tanımını temsil ederse doğru döndürür.|  
|<xref:System.Type.DeclaringMethod%2A>|Tür parametresi genel bir yöntemle tanımlanmamışsa, geçerli genel tür parametresini tanımlayan veya null'u tanımlayan genel yöntemi döndürür.|  
|<xref:System.Type.MakeGenericType%2A>|Geçerli genel tür tanımının tür parametreleri için bir dizi tür öğelerini yerine alır ve elde edilen yapılandırılan türü temsil eden bir <xref:System.Type> nesne döndürür.|  
  
 Buna ek olarak, <xref:System.Reflection.MethodInfo> sınıf üyeleri genel yöntemler için çalışma zamanı bilgilerini etkinleştirin. Genel <xref:System.Reflection.MethodBase.IsGenericMethod%2A> yöntemleri yansıtmak için kullanılan terimler için değişmez koşulların listesi için özellik açıklamalarına bakın.  
  
|System.Reflection.MemberInfo Üye Adı|Açıklama|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Bir yöntem genelse doğru döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Oluşturulmuş genel yöntemin tür bağımsız değişkenlerini veya genel yöntem tanımının tür parametrelerini temsil eden bir tür nesne dizisi döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Geçerli oluşturulmuş yöntem için temel genel yöntem tanımını döndürür.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Yöntem veya çevreleyen türlerinden herhangi biri belirli türler için sağlanmadı herhangi bir tür parametreleri içeriyorsa doğru döndürür.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Geçerli <xref:System.Reflection.MethodInfo> genel bir yöntemin tanımını temsil ederse doğru döndürür.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Geçerli genel yöntem tanımının tür parametreleri için bir dizi tür öğelerini yerine alır ve elde edilen yapılandırılan yöntemi temsil eden bir <xref:System.Reflection.MethodInfo> nesne döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Genel Türler](../../../standard/generics/index.md)
