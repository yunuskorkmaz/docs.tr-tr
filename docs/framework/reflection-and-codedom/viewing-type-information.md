---
title: Tür Bilgilerini Görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e658b2c86eecdbc45a9adde8d28cfb890dd591b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956655"
---
# <a name="viewing-type-information"></a>Tür Bilgilerini Görüntüleme
<xref:System.Type?displayProperty=nameWithType> Sınıfı, yansıma için bir merkezidir. Ortak dil çalışma zamanı, yansıma istediğinde yüklenen bir tür için **türü** oluşturur. Bu tür hakkındaki her şeyi bulmak için bir **tür** nesnesinin yöntemlerini, alanlarını, özelliklerini ve iç içe geçmiş sınıfları kullanabilirsiniz.  
  
 Yüklü <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> olmayan <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> derlemelerden, istediğiniz tür veya türlerin adını geçirerek **tür** nesneleri almak için veya kullanın. Zaten <xref:System.Type.GetType%2A?displayProperty=nameWithType> yüklü olan bir derlemeden **tür** nesnelerini almak için kullanın. Modül <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> türü <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> nesneleri almak için ve kullanın.  
  
> [!NOTE]
> Genel türleri ve yöntemleri incelemek ve işlemek istiyorsanız, lütfen [yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) bölümünde sunulan ek bilgilere ve [nasıl yapılır: Yansıma](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)ile genel türleri Inceleyin ve örnek oluşturun.  
  
 Aşağıdaki örnek, bir derlemenin <xref:System.Reflection.Assembly> nesne ve modülünü almak için gereken söz dizimini gösterir.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Aşağıdaki örnekte, yüklü bir derlemeden **tür** nesnelerinin alınması gösterilmektedir.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Bir **türü**edindiğinizde, bu türden Üyeler hakkında bilgi bulmanın birçok yolu vardır. Örneğin, geçerli türdeki üyelerin her birini açıklayan bir <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.MemberInfo> nesne dizisi elde eden yöntemini çağırarak tüm tür üyeleri hakkında bilgi edinebilirsiniz.  
  
 Ayrıca, bir veya daha fazla Oluşturucu, yöntem, olay, alan veya ada göre belirttiğiniz özellikler hakkında bilgi almak için **tür** sınıfındaki yöntemleri de kullanabilirsiniz. Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> geçerli sınıfın belirli bir oluşturucusunu kapsüller.  
  
 Bir **tür**varsa, bu türü içeren modülü kapsülleyen bir <xref:System.Type.Module%2A?displayProperty=nameWithType> nesne almak için özelliğini kullanabilirsiniz. Modülünü içeren derlemeyi kapsülleyen bir nesneyi bulmak için özelliğinikullanın.<xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> <xref:System.Type.Assembly%2A?displayProperty=nameWithType> Özelliğini kullanarak türü sarmalayan derlemeyi doğrudan elde edebilirsiniz.  
  
## <a name="systemtype-and-constructorinfo"></a>System. Type ve ConstructorInfo  
 Aşağıdaki örnek, bu <xref:System.String> örnekte sınıfı için oluşturucuların nasıl ekleneceğini gösterir.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo ve PropertyInfo  
 , <xref:System.Reflection.MemberInfo>, Veya <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo>nesnelerini kullanarak türün yöntemleri, özellikleri, olayları ve alanları hakkında bilgi edinin. <xref:System.Reflection.PropertyInfo>  
  
 Aşağıdaki örnek, **System. IO. File** sınıfındaki üye sayısını listelemek için <xref:System.Type.IsPublic%2A> **MemberInfo** kullanır ve sınıfının görünürlüğünü öğrenmek için özelliğini kullanır.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Aşağıdaki örnek, belirtilen üyenin türünü araştırır. Bir **MemberInfo** için bir üye üzerinde yansıma gerçekleştirir ve türünü listeler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Aşağıdaki örnek, belirtilen sınıfın tüm üyelerini (oluşturucular, alanlar <xref:System.Reflection.BindingFlags> , özellikler, olaylar ve Yöntemler) listelemek ve üyeleri statik ve örneğe bölmek için ile birlikte tüm yansıma  **\*bilgileri** sınıflarını kullanır kategorisine.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
