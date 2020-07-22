---
title: Tür Bilgilerini Görüntüleme
description: .NET 'te yansıma için merkezi olan System. Type kullanarak tür bilgilerini görüntüleyin. ConstructorInfo, MemberInfo, MethodInfo, FieldInfo ve PropertyInfo bilgilerini inceleyin.
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
ms.openlocfilehash: cd74021e1f1a79626e171db13def98e546cd51df
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865209"
---
# <a name="viewing-type-information"></a>Tür Bilgilerini Görüntüleme
<xref:System.Type?displayProperty=nameWithType>Sınıfı, yansıma için bir merkezidir. Ortak dil çalışma zamanı, yansıma istediğinde yüklenen bir tür için **türü** oluşturur. Bu tür hakkındaki her şeyi bulmak için bir **tür** nesnesinin yöntemlerini, alanlarını, özelliklerini ve iç içe geçmiş sınıfları kullanabilirsiniz.  
  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> Yüklü olmayan derlemelerden, istediğiniz tür veya türlerin adını geçirerek **tür** nesneleri almak için veya kullanın. <xref:System.Type.GetType%2A?displayProperty=nameWithType>Zaten yüklü olan bir derlemeden **tür** nesnelerini almak için kullanın. <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> Modül **türü** nesneleri almak için ve kullanın.  
  
> [!NOTE]
> Genel türleri ve yöntemleri incelemek ve işlemek istiyorsanız, lütfen [yansıma ve genel türler](reflection-and-generic-types.md) ' de sunulan ek bilgilere ve [nasıl yapılır: yansıma Ile genel türleri Inceleme ve örnek oluşturma](how-to-examine-and-instantiate-generic-types-with-reflection.md)bölümüne bakın.  
  
 Aşağıdaki örnek, <xref:System.Reflection.Assembly> bir derlemenin nesne ve modülünü almak için gereken söz dizimini gösterir.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Aşağıdaki örnekte, yüklü bir derlemeden **tür** nesnelerinin alınması gösterilmektedir.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Bir **türü**edindiğinizde, bu türden Üyeler hakkında bilgi bulmanın birçok yolu vardır. Örneğin, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.MemberInfo> geçerli türdeki üyelerin her birini açıklayan bir nesne dizisi elde eden yöntemini çağırarak tüm tür üyeleri hakkında bilgi edinebilirsiniz.  
  
 Ayrıca, bir veya daha fazla Oluşturucu, yöntem, olay, alan veya ada göre belirttiğiniz özellikler hakkında bilgi almak için **tür** sınıfındaki yöntemleri de kullanabilirsiniz. Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> Geçerli sınıfın belirli bir oluşturucusunu kapsüller.  
  
 Bir **tür**varsa, <xref:System.Type.Module%2A?displayProperty=nameWithType> Bu türü içeren modülü kapsülleyen bir nesne almak için özelliğini kullanabilirsiniz. <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType>Modülünü içeren derlemeyi kapsülleyen bir nesneyi bulmak için özelliğini kullanın. Özelliğini kullanarak türü sarmalayan derlemeyi doğrudan elde edebilirsiniz <xref:System.Type.Assembly%2A?displayProperty=nameWithType> .  
  
## <a name="systemtype-and-constructorinfo"></a>System. Type ve ConstructorInfo  
 Aşağıdaki örnek, bu örnekte sınıfı için oluşturucuların nasıl ekleneceğini gösterir <xref:System.String> .  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo ve PropertyInfo  
 ,, Veya nesnelerini kullanarak türün yöntemleri, özellikleri, olayları ve alanları hakkında bilgi <xref:System.Reflection.MemberInfo> edinin <xref:System.Reflection.MethodInfo> <xref:System.Reflection.FieldInfo> <xref:System.Reflection.PropertyInfo> .  
  
 Aşağıdaki örnek, **System. IO. File** sınıfındaki üye sayısını listelemek için **MemberInfo** kullanır ve <xref:System.Type.IsPublic%2A> sınıfının görünürlüğünü öğrenmek için özelliğini kullanır.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Aşağıdaki örnek, belirtilen üyenin türünü araştırır. Bir **MemberInfo** için bir üye üzerinde yansıma gerçekleştirir ve türünü listeler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Aşağıdaki örnek, ** \* ** <xref:System.Reflection.BindingFlags> belirtilen sınıfın tüm üyelerini (oluşturucular, alanlar, özellikler, olaylar ve Yöntemler) listelemek ve üyeleri statik ve örnek kategorilerine bölmek Için ile birlikte tüm yansıma bilgileri sınıflarını kullanır.  
  
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
- [Yansıma ve Genel Türler](reflection-and-generic-types.md)
