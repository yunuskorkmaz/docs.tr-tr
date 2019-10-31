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
ms.openlocfilehash: fe5bb95d5e1f90c0dafa30977d76ea1d62125c99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130888"
---
# <a name="retrieving-information-stored-in-attributes"></a>Özniteliklerde Depolanan Bilgileri Alma
Özel bir özniteliğin alınması basit bir işlemdir. İlk olarak, almak istediğiniz özniteliğin bir örneğini bildirin. Ardından, yeni özniteliğini almak istediğiniz özniteliğin değerine başlatmak için <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> yöntemini kullanın. Yeni özniteliği başlatıldıktan sonra, değerlerini almak için özelliklerini kullanmanız yeterlidir.  
  
> [!IMPORTANT]
> Bu konu, yürütme bağlamına yüklenen kodun özniteliklerinin nasıl alınacağını açıklar. Yalnızca yansıma bağlamına yüklenen kodun özniteliklerini almak için <xref:System.Reflection.CustomAttributeData> sınıfını, [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)bölümünde gösterildiği gibi kullanmanız gerekir.  
  
 Bu bölümde özniteliklerin alınması için aşağıdaki yollar açıklanmaktadır:  
  
- [Bir özniteliğin tek bir örneğini alma](#cpconretrievingsingleinstanceofattribute)  
  
- [Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Bir özniteliğin tek bir örneğini alma  
 Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanan) sınıf düzeyindeki `MainApp` sınıfına uygulanır. `GetAttribute` yöntemi, konsol içine görüntülemeden önce sınıf düzeyinde `DeveloperAttribute` depolanan değerleri almak için **GetCustomAttribute** kullanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Bu program yürütüldüğünde aşağıdaki metni görüntüler.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Öznitelik bulunamazsa **GetCustomAttribute** yöntemi null bir değere `MyAttribute` başlatır. Bu örnek, böyle bir örnek için `MyAttribute` denetler ve hiçbir öznitelik bulunamazsa kullanıcıya bildirir. `DeveloperAttribute` sınıf kapsamında bulunmazsa, aşağıdaki ileti konsola görüntülenir.  
  
```console  
The attribute was not found.   
```  
  
 Bu örnek, öznitelik tanımının geçerli ad alanında olduğunu varsayar. Geçerli ad alanında değilse öznitelik tanımının bulunduğu ad alanını içeri aktarmayı unutmayın.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma  
 Önceki örnekte, incelenecek sınıf ve bulunacak özel öznitelik <xref:System.Attribute.GetCustomAttribute%2A>geçirilir. Bu kod, sınıf düzeyinde bir özniteliğin yalnızca bir örneği uygulandığında iyi bir şekilde çalışacaktır. Ancak, aynı sınıf düzeyinde bir özniteliğin birden çok örneği uygulanırsa **GetCustomAttribute** yöntemi tüm bilgileri almaz. Aynı özniteliğin birden fazla örneğinin aynı kapsama uygulandığı durumlarda, bir özniteliğin tüm örneklerini bir diziye yerleştirmek için <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> kullanabilirsiniz. Örneğin, iki `DeveloperAttribute` örneği aynı sınıfın sınıf düzeyinde uygulanırsa, `GetAttribute` yöntemi her iki özniteliklerde bulunan bilgileri görüntüleyecek şekilde değiştirilebilir. Aynı düzeyde birden fazla öznitelik uygulamak için, <xref:System.AttributeUsageAttribute>özniteliğin **AllowMultiple** özelliği **true** olarak ayarlanmış şekilde tanımlanması gerektiğini unutmayın.  
  
 Aşağıdaki kod örneği, belirli bir sınıftaki tüm `DeveloperAttribute` örneklerine başvuran bir dizi oluşturmak için **GetCustomAttributes** yönteminin nasıl kullanılacağını gösterir. Tüm özniteliklerin değerleri daha sonra konsola görüntülenir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Hiçbir öznitelik bulunamazsa, bu kod kullanıcıyı uyarır. Aksi halde, her iki `DeveloperAttribute` örneğinde bulunan bilgiler görüntülenir.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma  
 <xref:System.Attribute.GetCustomAttributes%2A> ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri bir sınıfın tamamını aramaz ve bu sınıftaki bir özniteliğin tüm örneklerini döndürmez. Bunun yerine, tek seferde yalnızca bir belirtilen yöntemi veya üyeyi arar. Her üyeye uygulanmış aynı özniteliğe sahip bir sınıfınız varsa ve bu üyelere uygulanan tüm özniteliklerin değerlerini almak istiyorsanız, her yöntemi veya üyeyi **GetCustomAttributes** ve GetCustomAttribute için tek tek sağlamalısınız.  
  
 Aşağıdaki kod örneği bir sınıfı parametre olarak alır ve sınıf düzeyinde ve bu sınıfın her bir yöntemi üzerinde `DeveloperAttribute` (daha önce tanımlanan) arar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Yöntem düzeyinde veya sınıf düzeyinde `DeveloperAttribute` bir örneği bulunamazsa, `GetAttribute` yöntemi kullanıcıya hiçbir öznitelik bulunamadığını bildirir ve özniteliği içermeyen yöntemin veya sınıfın adını görüntüler. Bir öznitelik bulunursa, `Name`, `Level`ve `Reviewed` alanları konsola görüntülenir.  
  
 Geçirilen sınıftaki tek tek yöntemleri ve üyeleri almak için <xref:System.Type> sınıfının üyelerini kullanabilirsiniz. Bu örnek öncelikle sınıf düzeyi için öznitelik bilgilerini almak üzere **tür** nesnesini sorgular. Sonra, yöntem düzeyi için öznitelik bilgilerini almak üzere tüm yöntemlerin örneklerini bir <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> nesneleri dizisine yerleştirmek için <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> kullanır. Ayrıca, özellik düzeyindeki öznitelikleri denetlemek için <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> yöntemini veya Oluşturucu düzeyindeki öznitelikleri denetlemek için <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Öznitelikler](../../../docs/standard/attributes/index.md)
