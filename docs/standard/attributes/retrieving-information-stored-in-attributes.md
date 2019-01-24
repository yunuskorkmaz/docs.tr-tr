---
title: Özniteliklerde Depolanan Bilgileri Alma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d921c13765f5d61ce9822df0b4059b2cf93a6f6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744095"
---
# <a name="retrieving-information-stored-in-attributes"></a>Özniteliklerde Depolanan Bilgileri Alma
Özel bir öznitelik alma basit bir işlemdir. Öncelikle, almak istediğiniz öznitelik örneği bildirin. Ardından, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> almak istediğiniz özniteliğinin değeri için yeni öznitelik başlatmak için yöntemi. Yeni öznitelik başlatıldıktan sonra sadece özellikleri değerlerini almak için kullanın.  
  
> [!IMPORTANT]
>  Bu konu, kod yürütme bağlamı yüklenen öznitelikleri almak açıklar. Salt yansıma bağlamına yüklenen kod öznitelikleri almak için kullanmanız gerekir <xref:System.Reflection.CustomAttributeData> gösterildiği gibi sınıf [nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Bu bölümde, öznitelikleri almak için aşağıdaki yöntemleri açıklanmaktadır:  
  
-   [Tek bir örneği bir öznitelik alma](#cpconretrievingsingleinstanceofattribute)  
  
-   [Birden fazla aynı kapsam için uygulanan bir öznitelik alma](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Birden çok örneğini farklı kapsamlara uygulanan bir öznitelik alma](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Tek bir örneği bir öznitelik alma  
 Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanmıştır) uygulanan `MainApp` sınıf düzeyinde sınıfı. `GetAttribute` Yöntemi kullanan **GetCustomAttribute** depolanan değerleri almak için `DeveloperAttribute` bunları konsola göstermeden önce sınıf düzeyinde.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Bu program çalıştırıldığında aşağıdaki metni görüntüler.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Öznitelik bulunamazsa **GetCustomAttribute** yöntemi başlatır `MyAttribute` bir null değer. Bu örnek denetler `MyAttribute` bu tür bir örnek için ve bir öznitelik yok bulunursa kullanıcıyı uyarır. Varsa `DeveloperAttribute` bulunamadı sınıf kapsamında aşağıdaki iletiyi konsola görüntüler.  
  
```  
The attribute was not found.   
```  
  
 Bu örnekte, öznitelik tanımı geçerli bir ad alanında olduğunu varsayar. Geçerli bir ad alanında değilse, öznitelik tanımı bulunduğu ad alanı almayı unutmayın.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Birden fazla aynı kapsam için uygulanan bir öznitelik alma  
 Önceki örnekte, inceleme sınıfı ve bulmak için özel öznitelik geçirilen <xref:System.Attribute.GetCustomAttribute%2A>. Bu kod, bir özniteliğin bir örnek sınıf düzeyinde de uygulanır, yalnızca çalışır. Ancak, bir özniteliğin birden çok örneği aynı sınıf düzeyinde uygulanmışsa **GetCustomAttribute** yöntemi tüm bilgileri alamadı. Aynı öznitelik birden çok örneğini aynı kapsama uygulanır olduğu durumlarda, kullandığınız <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> bir özniteliğin tüm örnekleri bir dizi içine yerleştirmek için. Örneğin, iki örneklerini `DeveloperAttribute` aynı sınıfın sınıf düzeyinde uygulanan `GetAttribute` yöntemi, her iki öznitelikleri içinde bulunan bilgileri görüntülemek için değiştirilebilir. Unutmayın aynı düzeyde birden çok öznitelik uygulamak için özniteliği ile tanımlanmalıdır **AttributeUsage** özelliğini **true** içinde <xref:System.AttributeUsageAttribute>.  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir **GetCustomAttributes** tüm örneklerini başvuran bir dizi oluşturmak için gereken yöntemini `DeveloperAttribute` birinde sınıfı verilir. Tüm özniteliklerinin değerlerini sonra konsolda görüntülenir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Hiç öznitelik bulunamadı, bu kod, kullanıcıyı uyarır. Aksi takdirde, bilgileri bulunan iki örneklerine `DeveloperAttribute` görüntülenir.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Birden çok örneğini farklı kapsamlara uygulanan bir öznitelik alma  
 <xref:System.Attribute.GetCustomAttributes%2A> Ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri değil sınıfının tümüne arayın ve bu sınıfta bir öznitelik tüm örneklerini döndürür. Bunun yerine, bunlar yalnızca bir belirtilen yöntem veya üye aynı anda arayın. Bir sınıf her üyeye uygulanan aynı özniteliğe sahip ve bu üyeler için uygulanan tüm öznitelikleri değerleri almak istediğiniz her bir yöntem veya üye için ayrı ayrı sağlamanız gerekir **GetCustomAttributes** ve  **GetCustomAttribute**.  
  
 Aşağıdaki kod örneği, bir sınıf bir parametre olarak alır ve arar `DeveloperAttribute` (tanımlanan önceden) Sınıf düzeyinde ve söz konusu sınıfın tek tek her yöntemi.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Örneği, `DeveloperAttribute` yöntem düzeyine ya da sınıf düzeyinde bulunan `GetAttribute` yöntemi hiçbir öznitelik bulunamadı kullanıcıya bildirir ve yöntem veya özniteliği içermiyor, sınıf adını görüntüler. Bir öznitelik bulunursa `Name`, `Level`, ve `Reviewed` alanları, konsolda görüntülenir.  
  
 Üyelerinin kullanabileceği <xref:System.Type> geçirilen sınıfı üyeleri ve her bir yöntem almak için sınıf. Bu örnekte ilk sorgular **türü** sınıf düzeyinde için öznitelik bilgileri almak için nesne. Ardından, kullanır <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tüm yöntemleri örnekleri bir dizi içine yerleştirmek için <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> nesneleri yöntem düzeyine öznitelik bilgileri alınamıyor. Ayrıca <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> özellik düzeyinde öznitelikler için denetlenecek yöntemi veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> Oluşturucusu düzeyindeki öznitelikler denetlemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Öznitelikler](../../../docs/standard/attributes/index.md)
