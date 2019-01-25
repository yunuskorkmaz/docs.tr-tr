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
ms.openlocfilehash: 267102198731054bd2ce050299627eecbd37a4a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692222"
---
# <a name="viewing-type-information"></a>Tür Bilgilerini Görüntüleme
<xref:System.Type?displayProperty=nameWithType> Sınıfı, yansıma için merkezi. Ortak dil çalışma zamanı oluşturur **türü** yansıma istediğinde yüklenen bir türü için. Kullanabileceğiniz bir **türü** nesnenin yöntemler, alanlar, özellikler ve türü hakkında her şeyi öğrenmek için iç içe geçmiş sınıflar.  
  
 Kullanım <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> almak için **türü** nesneleri derlemelerden, türü veya türleri istediğiniz geçirme yüklenmedi. Kullanım <xref:System.Type.GetType%2A?displayProperty=nameWithType> almak için **türü** nesneleri bir derlemeden zaten yüklendi. Kullanım <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> modülü edinme **türü** nesneleri.  
  
> [!NOTE]
>  Sağlanan ek bilgileri incelemek ve genel türler ve yöntemlerin işlemek istiyorsanız, lütfen bkz [yansıma ve genel türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) ve [nasıl yapılır: İnceleme ve örnek oluşturma yansıma ile genel türleri](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Aşağıdaki örnek almak gerekli söz dizimi görülmektedir <xref:System.Reflection.Assembly> nesnesi ve bir birleştirme modülü.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 Aşağıdaki örnek alma gösterir **türü** nesnelerden yüklenen derleme.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Edindikten sonra bir **türü**, bu tür üyeleri hakkında bilgi bulabilir birçok yolu vardır. Örneğin, türün tüm üyeleri hakkında çağırarak bilgi edinebilirsiniz <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> dizisi alır yöntemi <xref:System.Reflection.MemberInfo> her biri geçerli tür üyelerini tanımlayan nesne.  
  
 Üzerinde yöntemleri kullanabilirsiniz **türü** bir veya daha fazla Oluşturucular, yöntemler, olaylar, alanlar veya ada göre belirten özellikleri hakkında bilgi almak için sınıf. Örneğin, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> geçerli sınıfın belirli bir oluşturucu kapsüller.  
  
 Varsa bir **türü**, kullanabileceğiniz <xref:System.Type.Module%2A?displayProperty=nameWithType> bu türü içeren modül kapsülleyen bir nesnenin alınacağı özellik. Kullanım <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> modülü içeren derlemenin yalıtan bir nesneyi bulmak için özellik. Kullanarak doğrudan türü sarmalayan derleme edinebilirsiniz <xref:System.Type.Assembly%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type ve ConstructorInfo  
 Aşağıdaki örnek, bir sınıf, bu durumda, için oluşturucular listelemek gösterilmektedir <xref:System.String> sınıfı.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo FieldInfo ve PropertyInfo  
 Türün yöntemleri, özellikleri, olayları ve alanları kullanma hakkında bilgi edinmek <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, veya <xref:System.Reflection.PropertyInfo> nesneleri.  
  
 Aşağıdaki örnekte **MemberInfo** üye sayısı listelemek için **System.IO.File** sınıfı ve kullanımları <xref:System.Type.IsPublic%2A> özelliği sınıfı görünürlüğünü belirler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 Aşağıdaki örnek belirtilen üyenin türü araştırır. Bir üye üzerinde yansıma gerçekleştirir **MemberInfo** sınıfı ve türünü listeler.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 Aşağıdaki örnek, tüm yansıma kullanır  **\*bilgisi** ile birlikte sınıfları <xref:System.Reflection.BindingFlags> üyeleri bölme tüm üyeleri (Oluşturucular, alanları, özellikleri, olayları ve yöntemleri) belirtilen sınıfın listelemek için içine statik ve örnek kategorisi.  
  
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
