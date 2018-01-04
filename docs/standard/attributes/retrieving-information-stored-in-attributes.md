---
title: "Özniteliklerde Depolanan Bilgileri Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 146572fb060d1bd37d6eee5b5dce3c255b28f8b2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>Özniteliklerde Depolanan Bilgileri Alma
Özel bir öznitelik alma basit bir işlemdir. Öncelikle, almak istediğiniz öznitelik örneği bildirin. Ardından, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> yöntemi almak istediğiniz özniteliğinin değeri için yeni öznitelik başlatılamadı. Yeni öznitelik başlatıldıktan sonra yalnızca özelliklerini değerleri almak için kullanın.  
  
> [!IMPORTANT]
>  Bu konu, yürütme bağlamına yüklenen kod için özniteliklerini Al açıklar. Salt yansıma bağlamına yüklenen kod öznitelikleri almak için kullanmanız gerekir <xref:System.Reflection.CustomAttributeData> gösterildiği gibi sınıfı [nasıl yapılır: yük derlemelerine Reflection-Only bağlamı](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Bu bölüm öznitelikleri almak için aşağıdaki yöntemleri açıklar:  
  
-   [Bir öznitelik tek bir örneğini alma](#cpconretrievingsingleinstanceofattribute)  
  
-   [Birden çok örneğini aynı kapsama uygulanan bir öznitelik alınıyor](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Birden çok örneğini farklı kapsamlar için uygulanan bir öznitelik alınıyor](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Bir öznitelik tek bir örneğini alma  
 Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanan) uygulanan `MainApp` sınıf düzeyinde sınıfı. `GetAttribute` Yöntemi kullanan **GetCustomAttribute** depolanan değerleri almak için `DeveloperAttribute` konsola göstermeden önce sınıfı düzeyi.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Bu program çalıştırıldığında aşağıdaki metni görüntüler.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Öznitelik bulunmazsa **GetCustomAttribute** yöntemi başlatır `MyAttribute` bir null değer. Bu örnek denetler `MyAttribute` böyle bir örneği için ve hiçbir öznitelik bulunursa, kullanıcıya bildirir. Varsa `DeveloperAttribute` bulunamadı sınıfı kapsamda aşağıdaki iletiyi konsola görüntüler.  
  
```  
The attribute was not found.   
```  
  
 Bu örnekte, öznitelik tanımı geçerli ad alanında olduğunu varsayar. Geçerli ad alanında değilse, öznitelik tanımı bulunduğu ad alanı içe aktarmayı unutmayın.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Birden çok örneğini aynı kapsama uygulanan bir öznitelik alınıyor  
 Önceki örnekte incelemek için sınıf ve bulmak için belirli öznitelik geçirilecek <xref:System.Attribute.GetCustomAttribute%2A>. Bu kod, bir öznitelik bir örneği üzerinde sınıf düzeyinde iyi uygulanan yalnızca çalışır. Ancak, bir öznitelik birden çok örneğini aynı sınıf düzeyinde uyguladıysanız **GetCustomAttribute** yöntemi tüm bilgileri alamadı. Aynı öznitelik birden çok örneğini aynı kapsama uygulanır olduğu durumlarda, kullandığınız <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> bir öznitelik tüm örnekleri bir dizi içine yerleştirilecek. Örneğin, iki örneklerini `DeveloperAttribute` aynı sınıfı sınıf düzeyinde uygulanır `GetAttribute` yöntemi, her iki öznitelik içinde bulunan bilgileri görüntülemek için değiştirilebilir. Aynı düzeyde birden çok öznitelik uygulanacağını unutmayın özniteliği ile tanımlanmalıdır **AttributeUsage** özelliğini **true** içinde <xref:System.AttributeUsageAttribute>.  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir **GetCustomAttributes** tüm örneklerini başvuruda bulunan bir dizi oluşturmak için yöntemi `DeveloperAttribute` birinde sınıfı verilir. Tüm öznitelik değerleri daha sonra konsola görüntülenir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Hiçbir öznitelik bulunamazsa, bu kod kullanıcıyı uyarır. Aksi takdirde, bilgi bulunan her iki örneklerine `DeveloperAttribute` görüntülenir.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Birden çok örneğini farklı kapsamlar için uygulanan bir öznitelik alınıyor  
 <xref:System.Attribute.GetCustomAttributes%2A> Ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri değil tüm sınıf arama ve bu sınıfta bir öznitelik tüm örneklerini döndürür. Bunun yerine, bunlar yalnızca bir belirtilen yöntem veya üye aynı anda arayın. Her üyeye uygulanan aynı özniteliği bir sınıf varsa ve bu üyelere uygulanan tüm öznitelikleri değerleri almak istediğiniz her bir yöntemi veya üye için ayrı ayrı sağlamanız gerekir **GetCustomAttributes** ve  **GetCustomAttribute**.  
  
 Aşağıdaki kod örneğinde bir sınıf bir parametre olarak alır ve arar `DeveloperAttribute` (tanımlanan önceden) Sınıf düzeyinde ve bu sınıfın tek tek her yöntemi.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Hiçbir örneği varsa `DeveloperAttribute` yöntemi düzeyi veya sınıf düzeyinde bulunan `GetAttribute` yöntemi hiç öznitelik bulunamadı kullanıcıyı uyarır ve yöntem veya öznitelik içermiyor sınıf adını görüntüler. Bir öznitelik bulunursa, `Name`, `Level`, ve `Reviewed` alanları, konsolda görüntülenir.  
  
 Üyeleri kullanabilir <xref:System.Type> üyeleri ve tek tek yöntemler geçirilen sınıfında almak için sınıf. Bu örnek ilk sorgular **türü** sınıf düzeyinde için öznitelik bilgileri almak için nesne. Ardından, kullanan <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tüm yöntemleri örnekleri bir dizi içine yerleştirilecek <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> yöntemi düzeyi için öznitelik bilgileri almak için nesneleri. De kullanabilirsiniz <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> özelliği düzeyindeki öznitelikler denetlemek için yöntemi veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> Oluşturucusu düzeyindeki öznitelikler denetlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Öznitelikler](../../../docs/standard/attributes/index.md)
