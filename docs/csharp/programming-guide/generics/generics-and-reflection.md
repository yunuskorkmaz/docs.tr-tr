---
title: Genel türler ve yansıma-C# Programlama Kılavuzu
description: Genel türler hakkında bilgi edinmek için yansıma kullanma hakkında bilgi edinin. Genel yansıma için hüküm ve koşulların listesini görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
ms.openlocfilehash: 6e4387fe7e78cd0e970531ae42f323efa8f181db
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299311"
---
# <a name="generics-and-reflection-c-programming-guide"></a>Genel Türler ve Yansıma (C# Programlama Kılavuzu)
Ortak dil çalışma zamanı (CLR) çalışma zamanında genel tür bilgilerine erişime sahip olduğu için, genel türler hakkında genel türler hakkında bilgi edinmek için yansımayı genel olmayan türler ile aynı şekilde elde edebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).  
  
 .NET Framework 2,0 ' de, <xref:System.Type> Genel türler için çalışma zamanı bilgilerini etkinleştirmek üzere sınıfa birkaç yeni üye eklenmiştir. Bu yöntemlerin ve özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bu sınıfların belgelerine bakın. <xref:System.Reflection.Emit>Ad alanı Ayrıca, genel türleri destekleyen yeni üyeler içerir. Bkz. [nasıl yapılır: yansıma yayma Ile genel tür tanımlama](../../../framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
 Genel yansıma ' de kullanılan koşullara yönelik sabit koşulların bir listesi için, bkz <xref:System.Type.IsGenericType%2A> . Özellik açıklamaları.  
  
|System. Type üye adı|Description|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Bir tür genel ise true döndürür.|  
|<xref:System.Type.GetGenericArguments%2A>|`Type`Oluşturulmuş bir tür için sağlanan tür bağımsız değişkenlerini veya bir genel tür tanımının tür parametrelerini temsil eden nesne dizisini döndürür.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Geçerli oluşturulmuş tür için temel alınan genel tür tanımını döndürür.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|`Type`Geçerli genel tür parametresindeki kısıtlamaları temsil eden nesne dizisini döndürür.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Türü veya kapsayan türleri ya da metotlarından herhangi biri, belirli türler sağlanmadığından tür parametreleri içeriyorsa true değerini döndürür.|  
|<xref:System.Type.GenericParameterAttributes%2A>|`GenericParameterAttributes`Geçerli genel tür parametresinin özel kısıtlamalarını tanımlayan bayrakların bir birleşimini alır.|  
|<xref:System.Type.GenericParameterPosition%2A>|`Type`Bir tür parametresini temsil eden bir nesne için, tür parametresinin konumunu, genel tür tanımının tür parametresi listesinde veya tür parametresini tanımlayan genel yöntem tanımının türü olarak alır.|  
|<xref:System.Type.IsGenericParameter%2A>|Geçerli `Type` öğesinin bir genel tür veya yöntem tanımının tür parametresini temsil ettiğini gösteren bir değer alır.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Geçerli öğesinin, <xref:System.Type> diğer genel türlerin üzerinde oluşturulabilecek genel bir tür tanımını temsil edip etmediğini belirten bir değer alır. Tür genel bir türün tanımını temsil ediyorsa, true döndürür.|  
|<xref:System.Type.DeclaringMethod%2A>|Geçerli genel tür parametresini tanımlayan genel yöntemi veya tür parametresi genel bir yöntem tarafından tanımlanmamışsa null değerini döndürür.|  
|<xref:System.Type.MakeGenericType%2A>|Geçerli genel tür tanımının tür parametreleri için bir tür dizisinin öğelerini değiştirir ve <xref:System.Type> elde edilen oluşturulan türü temsil eden bir nesne döndürür.|  
  
 Ayrıca, sınıfının üyeleri, <xref:System.Reflection.MethodInfo> genel metotlar için çalışma zamanı bilgilerini etkinleştirir. <xref:System.Reflection.MethodBase.IsGenericMethod%2A>Genel yöntemleri yansıtmak için kullanılan koşullara yönelik sabit koşulların bir listesi için bkz. Özellik açıklamaları.  
  
|System. Reflection. MemberInfo üye adı|Description|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodBase.IsGenericMethod%2A>|Bir yöntem genel ise, true döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Oluşturulmuş bir genel metodun tür bağımsız değişkenlerini veya bir genel yöntem tanımının tür parametrelerini temsil eden nesne türünde bir dizi döndürür.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Geçerli oluşturulan yöntem için temeldeki genel yöntem tanımını döndürür.|  
|<xref:System.Reflection.MethodBase.ContainsGenericParameters%2A>|Yöntem veya kapsayan türlerinden herhangi biri, belirli türler sağlanmadığından herhangi bir tür parametresi içeriyorsa true değerini döndürür.|  
|<xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>|Geçerli <xref:System.Reflection.MethodInfo> bir genel yöntemin tanımını temsil ediyorsa, true döndürür.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Geçerli genel yöntem tanımının tür parametreleri için bir tür dizisinin öğelerini değiştirir ve <xref:System.Reflection.MethodInfo> elde edilen oluşturulmuş yöntemi temsil eden bir nesne döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türler](./index.md)
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Genel Türler](../../../standard/generics/index.md)
