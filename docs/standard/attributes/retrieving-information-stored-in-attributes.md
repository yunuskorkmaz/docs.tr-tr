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
ms.openlocfilehash: 4f0f3555ae1ab7e662d5f88ac65739a7c791a964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78158083"
---
# <a name="retrieving-information-stored-in-attributes"></a>Özniteliklerde Depolanan Bilgileri Alma
Özel bir öznitelik alma basit bir işlemdir. İlk olarak, almak istediğiniz özniteliğin bir örneğini bildirin. Ardından, almak <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> istediğiniz öznitelik değerine yeni öznitelik initialisegetirmek için yöntemi kullanın. Yeni öznitelik baş harfe getize edildikten sonra, değerleri almak için özelliklerini kullanmanız yeterlidir.  
  
> [!IMPORTANT]
> Bu konu, yürütme bağlamına yüklenen kod için öznitelikleri nasıl alındığını açıklar. Yalnızca yansıma bağlamına yüklenen kod için öznitelikleri <xref:System.Reflection.CustomAttributeData> almak için, [nasıl kullanılır: Derlemeleri Yalnızca Yansıma Bağlamına](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)Yükleyin'de gösterildiği gibi sınıfı kullanmanız gerekir.  
  
 Bu bölümde öznitelikleri almak için aşağıdaki yolları açıklanır:  
  
- [Öznitelik tek bir örnek alma](#cpconretrievingsingleinstanceofattribute)  
  
- [Aynı kapsama uygulanan bir öznitelik için birden çok örnek alma](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [Farklı kapsamlara uygulanan bir öznitelik için birden çok örnek alma](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Bir Öznitelik Tek Bir Örnek Alma  
 Aşağıdaki örnekte, `DeveloperAttribute` (önceki bölümde açıklanan) sınıf düzeyinde `MainApp` sınıfa uygulanır. Yöntem, `GetAttribute` konsola görüntülemeden önce sınıf düzeyinde `DeveloperAttribute` depolanan değerleri almak için **GetCustomAttribute** kullanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Bu program yürütüldüğünde aşağıdaki metni görüntüler.  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Öznitelik bulunamazsa, **GetCustomAttribute** yöntemi null `MyAttribute` değerine başlanır. Bu örnek, böyle bir örneği denetler `MyAttribute` ve öznitelik bulunamazsa kullanıcıyı not eder. Sınıf `DeveloperAttribute` kapsamında bulunmazsa, aşağıdaki ileti konsola görüntülenir.  
  
```console  
The attribute was not found.
```  
  
 Bu örnek, öznitelik tanımının geçerli ad alanında olduğunu varsayar. Geçerli ad alanında değilse öznitelik tanımının bulunduğu ad alanını içeri aktarmayı unutmayın.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Aynı Kapsama Uygulanan Bir Özniteliğin Birden Çok Örneğini Alma  
 Önceki örnekte, denetlenecek sınıf ve bulunacak özel <xref:System.Attribute.GetCustomAttribute%2A>nitelik. Sınıf düzeyinde bir öznitelik yalnızca bir örneği uygulanırsa bu kod iyi çalışır. Ancak, aynı sınıf düzeyinde bir öznitelik birden çok örnek uygulanırsa, **GetCustomAttribute** yöntemi tüm bilgileri almaz. Aynı öznitelikteki birden çok örneğin aynı kapsama uygulandığı durumlarda, <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> bir öznitelik teki tüm örnekleri bir diziye yerleştirmek için kullanabilirsiniz. Örneğin, aynı sınıfın sınıf `DeveloperAttribute` düzeyinde iki örnek uygulanırsa, `GetAttribute` yöntem her iki özetmende bulunan bilgileri görüntülemek için değiştirilebilir. Unutmayın, aynı düzeyde birden çok öznitelik uygulamak için öznitelik ' de **geçerli** <xref:System.AttributeUsageAttribute>olmak üzere **AllowMultiple** özelliği kümesi ile tanımlanması gerekir.  
  
 Aşağıdaki kod örneği, **getCustomAttributes** yönteminin, belirli bir sınıftaki tüm `DeveloperAttribute` örneklere başvuran bir dizi oluşturmak için nasıl kullanılacağını gösterir. Tüm özniteliklerin değerleri daha sonra konsola görüntülenir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Öznitelik bulunamazsa, bu kod kullanıcıyı uyarır. Aksi takdirde, her iki durumda `DeveloperAttribute` da bulunan bilgiler görüntülenir.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Farklı Kapsamlara Uygulanan Bir Özniteliğin Birden Çok Örneğini Alma  
 Ve <xref:System.Attribute.GetCustomAttributes%2A> <xref:System.Attribute.GetCustomAttribute%2A> yöntemler tüm sınıfı aramaz ve o sınıftaki öznitelik tüm örneklerini döndürmez. Bunun yerine, aynı anda yalnızca bir belirtilen yöntemi veya üyeyi ararlar. Her üyeye uygulanan aynı öznitelikte bir sınıfa sahipseniz ve bu üyelere uygulanan tüm özniteliklerdeki değerleri almak istiyorsanız, **getCustomAttributes** ve **GetCustomAttribute'a**her yöntemi veya üyeyi tek tek sağlamanız gerekir.  
  
 Aşağıdaki kod örneği bir sınıfparametre olarak alır `DeveloperAttribute` ve sınıf düzeyinde ve o sınıfın her bir yönteminde (daha önce tanımlanmış) arar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Yöntem düzeyinde veya `DeveloperAttribute` sınıf düzeyinde hiçbir örnek bulunmuyorsa, `GetAttribute` yöntem kullanıcıya öznitelik bulunmadığını gösterir ve özniteliği içermeyen yöntemin veya sınıfın adını görüntüler. Bir öznitelik `Name`bulunursa, `Level`, `Reviewed` ve alanlar konsola görüntülenir.  
  
 Geçen sınıfta tek tek <xref:System.Type> yöntemleri ve üyeleri almak için sınıf üyelerini kullanabilirsiniz. Bu örnek, sınıf düzeyi için öznitelik bilgisi almak için önce **Tür** nesnesini sorgular. Daha sonra, <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> yöntem düzeyi için öznitelik bilgilerini <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> almak için tüm yöntemlerin örneklerini bir dizi nesneye yerleştirmek için kullanır. Yöntemi, <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> özellik düzeyindeözleri denetlemek veya <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> oluşturucu düzeyindeözleri denetlemek için de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Öznitelikler](../../../docs/standard/attributes/index.md)
