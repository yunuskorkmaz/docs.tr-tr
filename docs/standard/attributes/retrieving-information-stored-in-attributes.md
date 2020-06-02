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
ms.openlocfilehash: fc8dcb38471d80d01d1f87993783af3d24868506
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276141"
---
# <a name="retrieving-information-stored-in-attributes"></a>Özniteliklerde Depolanan Bilgileri Alma
Özel bir özniteliğin alınması basit bir işlemdir. İlk olarak, almak istediğiniz özniteliğin bir örneğini bildirin. Ardından, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> Yeni özniteliğini almak istediğiniz özniteliğin değerine başlatmak için yöntemini kullanın. Yeni özniteliği başlatıldıktan sonra, değerlerini almak için özelliklerini kullanmanız yeterlidir.  
  
> [!IMPORTANT]
> Bu konu, yürütme bağlamına yüklenen kodun özniteliklerinin nasıl alınacağını açıklar. Yalnızca yansıma bağlamına yüklenen kodun özniteliklerini almak için <xref:System.Reflection.CustomAttributeData> sınıfını, [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)bölümünde gösterildiği gibi kullanmanız gerekir.  
  
 Bu bölümde özniteliklerin alınması için aşağıdaki yollar açıklanmaktadır:  
  
- [Bir özniteliğin tek bir örneğini alma](#cpconretrievingsingleinstanceofattribute)  
  
- [Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Bir özniteliğin tek bir örneğini alma  
 Aşağıdaki örnekte, `DeveloperAttribute` sınıf düzeyindeki sınıfına (önceki bölümde açıklanan) uygulanır `MainApp` . `GetAttribute`Yöntemi, içinde depolanan değerleri konsola görüntülemeden önce sınıf düzeyinde elde etmek Için **GetCustomAttribute** kullanır `DeveloperAttribute` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Bu program yürütüldüğünde aşağıdaki metni görüntüler.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Özniteliği bulunamazsa **GetCustomAttribute** yöntemi `MyAttribute` null değer olarak başlatılır. Bu örnek, `MyAttribute` böyle bir örnek olup olmadığını denetler ve bir öznitelik bulunmazsa kullanıcıya bildirir. `DeveloperAttribute`Sınıf kapsamında bulunmazsa, aşağıdaki ileti konsola görüntülenir.  
  
```console  
The attribute was not found.
```  
  
 Bu örnek, öznitelik tanımının geçerli ad alanında olduğunu varsayar. Geçerli ad alanında değilse öznitelik tanımının bulunduğu ad alanını içeri aktarmayı unutmayın.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Aynı kapsama uygulanan bir özniteliğin birden fazla örneğini alma  
 Önceki örnekte, incelenecek sınıf ve bulunacak özel öznitelik geçirilir <xref:System.Attribute.GetCustomAttribute%2A> . Bu kod, sınıf düzeyinde bir özniteliğin yalnızca bir örneği uygulandığında iyi bir şekilde çalışacaktır. Ancak, aynı sınıf düzeyinde bir özniteliğin birden çok örneği uygulanırsa **GetCustomAttribute** yöntemi tüm bilgileri almaz. Aynı özniteliğin birden fazla örneğinin aynı kapsama uygulandığı durumlarda, <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> bir özniteliğin tüm örneklerini bir diziye yerleştirmek için kullanabilirsiniz. Örneğin, iki örneği `DeveloperAttribute` aynı sınıfın sınıf düzeyinde uygulanırsa, `GetAttribute` yöntemi her iki öznitelik de bulunan bilgileri görüntüleyecek şekilde değiştirilebilir. Aynı düzeyde birden fazla öznitelik uygulamak için, özniteliğinin **AllowMultiple** özelliği içinde **true** olarak ayarlanmış şekilde tanımlanması gerektiğini unutmayın <xref:System.AttributeUsageAttribute> .  
  
 Aşağıdaki kod örneği, belirli bir sınıftaki tüm örneklere başvuran bir dizi oluşturmak için **GetCustomAttributes** yönteminin nasıl kullanılacağını gösterir `DeveloperAttribute` . Tüm özniteliklerin değerleri daha sonra konsola görüntülenir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Hiçbir öznitelik bulunamazsa, bu kod kullanıcıyı uyarır. Aksi halde, her iki örneğinde bulunan bilgiler `DeveloperAttribute` görüntülenir.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Farklı kapsamlara uygulanan bir özniteliğin birden fazla örneğini alma  
 <xref:System.Attribute.GetCustomAttributes%2A>Ve <xref:System.Attribute.GetCustomAttribute%2A> yöntemleri bir sınıfın tamamını aramaz ve bu sınıftaki bir özniteliğin tüm örneklerini döndürmez. Bunun yerine, tek seferde yalnızca bir belirtilen yöntemi veya üyeyi arar. Her üyeye uygulanmış aynı özniteliğe sahip bir sınıfınız varsa ve bu üyelere uygulanan tüm özniteliklerin değerlerini almak istiyorsanız, her yöntemi veya üyeyi **GetCustomAttributes** ve **GetCustomAttribute**için tek tek sağlamalısınız.  
  
 Aşağıdaki kod örneği, bir sınıfı parametre olarak alır ve sınıf `DeveloperAttribute` düzeyinde ve bu sınıfın her bir yöntemi üzerinde (daha önceden tanımlanmış) için arama yapar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 `DeveloperAttribute`Yöntem düzeyinde veya sınıf düzeyinde bir örneği bulunamazsa, `GetAttribute` yöntemi kullanıcıya hiçbir öznitelik bulunamadığını bildirir ve özniteliği içermeyen yöntemin veya sınıfın adını görüntüler. Bir öznitelik bulunursa,, `Name` `Level` ve `Reviewed` alanları konsoluna görüntülenir.  
  
 <xref:System.Type>Geçirilen sınıftaki bireysel yöntemleri ve üyeleri almak için sınıfının üyelerini kullanabilirsiniz. Bu örnek öncelikle sınıf düzeyi için öznitelik bilgilerini almak üzere **tür** nesnesini sorgular. Sonra, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> Yöntem düzeyi için öznitelik bilgilerini almak üzere tüm yöntemlerin örneklerini bir nesne dizisine yerleştirmek için öğesini kullanır. Ayrıca, <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> özellik düzeyindeki öznitelikleri denetlemek veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> Oluşturucu düzeyindeki öznitelikleri denetlemek için yöntemini de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Öznitelikler](index.md)
