---
title: "Tür Bilgilerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f6051c3da274c6a8579516e073c0ea91a195d59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="viewing-type-information"></a>Tür Bilgilerini Görüntüleme
<xref:System.Type?displayProperty=nameWithType> Sınıfı için yansıma Merkezi. Ortak dil çalışma zamanı oluşturur **türü** yansıma istediğinde yüklenen bir türü. Kullanabileceğiniz bir **türü** nesnenin yöntemleri, alanları, özellikleri ve türü hakkında her şeyi öğrenmek için iç içe geçmiş sınıflar.  
  
 Kullanım <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> almak için **türü** , türü veya türleri istediğiniz adına geçirme yüklenmedi derlemelerden nesneleri. Kullanım <xref:System.Type.GetType%2A?displayProperty=nameWithType> almak için **türü** önceden yüklenen derleme nesneleri. Kullanım <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> modülü edinme **türü** nesneleri.  
  
> [!NOTE]
>  Sağlanan ek bilgileri inceleyin ve genel türler ve yöntemleri değiştirmek istiyorsanız, lütfen bkz [yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) ve [nasıl yapılır: inceleyin ve Instantiate genel türleriyansımaile](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki örnek sözdizimi almak gerekli gösterir <xref:System.Reflection.Assembly> nesne ve bir derlemenin modülü.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Aşağıdaki örnek, alma gösterir **türü** yüklenen derlemesinden nesneleri.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Edindikten sonra bir **türü**, bu türün üyeleri hakkında bilgi bulmak birçok yolu vardır. Örneğin, tüm tür üyeleri hakkında arayarak bulabilirsiniz <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> bir dizi edinir yöntemi <xref:System.Reflection.MemberInfo> her geçerli türü üyelerinin açıklayan nesneleri.  
  
 Üzerinde yöntemleri kullanabilirsiniz **türü** bir veya daha fazla Oluşturucular, yöntemleri, olayları, alanlar veya ada göre belirten özellikleri hakkında bilgi almak için sınıf. Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> geçerli sınıfın belirli bir oluşturucu yalıtır.  
  
 Varsa bir **türü**, kullanabileceğiniz <xref:System.Type.Module%2A?displayProperty=nameWithType> özelliği bu türü içeren modülü yalıtan bir nesne elde edilir. Kullanım <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> modülü içeren derlemenin yalıtan bir nesneyi bulmak için özellik. Türü kullanılarak doğrudan yalıtır derleme edinebilirsiniz <xref:System.Type.Assembly%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type ve ConstructorInfo  
 Aşağıdaki örnek, bir sınıf, bu durumda, Oluşturucular listelemek gösterilmiştir <xref:System.String> sınıfı.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo ve PropertyInfo  
 Tür yöntemler, özellikler, olayları ve alanları kullanma hakkında bilgi edinmek <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, veya <xref:System.Reflection.PropertyInfo> nesneleri.  
  
 Aşağıdaki örnek kullanır **MemberInfo** üye sayısı listelemek için **System.IO.File** sınıfı ve kullandığı <xref:System.Type.IsPublic%2A> özelliği sınıfı görünürlüğünü belirler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Aşağıdaki örnek, belirtilen üye türü araştırır. Yansıma bir üyesi yapar **MemberInfo** sınıfı ve türünü listeler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Aşağıdaki örnek, tüm yansıma kullanır  **\*bilgisi** ile birlikte sınıfları <xref:System.Reflection.BindingFlags> üyeleri bölme tüm üyelerini (Oluşturucular, alanlar, özellikleri, olayları ve yöntemleri) belirtilen sınıf listelemek için statik içine ve örneği kategoriler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.BindingFlags>  
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetFields%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.MemberInfo>  
 <xref:System.Reflection.ConstructorInfo>  
 <xref:System.Reflection.MethodInfo>  
 <xref:System.Reflection.FieldInfo>  
 <xref:System.Reflection.EventInfo>  
 <xref:System.Reflection.ParameterInfo>  
 [Yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
