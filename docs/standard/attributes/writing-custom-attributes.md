---
title: Özel Öznitelikler Yazma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b38aa643453d9ad853d0d17af0f1ddf2ba69d4a1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="writing-custom-attributes"></a>Özel Öznitelikler Yazma
Kendi özel öznitelikler tasarlamak için birçok yeni kavram ana gerekmez. Nesne odaklı programlama ile bilgi sahibiyseniz ve sınıflar tasarlamak nasıl biliyorsanız gerekli bilgi çoğunu zaten sahip. Özel öznitelikler sınıflardır doğrudan veya dolaylı olarak türetilen temelde geleneksel <xref:System.Attribute?displayProperty=nameWithType>. Yalnızca geleneksel sınıfları gibi özel öznitelikler veri depolanıp yöntemleri içerir.  
  
 Özel öznitelik sınıfları düzgün tasarlamak için birincil adımlar aşağıdaki gibidir:  
  
-   [AttributeUsageAttribute uygulama](#cpconapplyingattributeusageattribute)  
  
-   [Öznitelik sınıfı bildirme](#cpcondeclaringattributeclass)  
  
-   [Oluşturucuları bildirme](#cpcondeclaringconstructors)  
  
-   [Özellikleri bildirme](#cpcondeclaringproperties)  
  
 Bu bölümde bu adımların her biri açıklar ve ile sonucuna bir [özel öznitelik örnek](#cpconcustomattributeexample).  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a>AttributeUsageAttribute uygulama  
 Bir özel öznitelik bildirim **AttributeUsageAttribute**, bazı öznitelik sınıfı anahtar özelliklerini tanımlayan. Örneğin, özniteliğinizi diğer sınıflar tarafından devralınır veya öznitelik uygulanabilir hangi öğelerin belirtin belirtebilirsiniz. Aşağıdaki kod parçası nasıl kullanılacağı ortaya **AttributeUsageAttribute**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Özel öznitelikler oluşturma için önemli olan üç üyeler içeriyor: [AttributeTargets](#cpconwritingcustomattributesanchor1), [devralınan](#cpconwritingcustomattributesanchor2), ve [AttributeUsage](#cpconwritingcustomattributesanchor3).  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a>AttributeTargets üyesi  
 Önceki örnekte, **AttributeTargets.All** , bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir. Alternatif olarak, belirtebilirsiniz **AttributeTargets.Class**, özniteliğinizi yalnızca bir sınıfa uygulanabilir belirten veya **AttributeTargets.Method**, özniteliğinizi uygulanabilir belirten yalnızca bir yöntem. Tüm program öğelerinin açıklaması için bu şekilde özel bir öznitelik tarafından işaretlenebilir.  
  
 Birden çok örneğini geçebilen <xref:System.AttributeTargets>. Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntemini uygulanabilir belirtir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a>Devralınan özellik  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özelliği, özniteliğinizi özniteliğinizi uygulanan sınıflarından türetilmiş sınıflar tarafından devralınır olup olmadığını belirtir. Bu özellik ya da gereken bir **true** (varsayılan) veya **false** bayrağı. Örneğin, aşağıdaki örnekte, `MyAttribute` varsayılan sahip <xref:System.AttributeUsageAttribute.Inherited%2A> değerini **true**, sırada `YourAttribute` sahip bir <xref:System.AttributeUsageAttribute.Inherited%2A> değerini **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 İki öznitelik sonra bir yöntem temel sınıfta uygulanır `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Son olarak, sınıf `YourClass` temel sınıfından devralınan `MyClass`. Yöntem `MyMethod` gösterir `MyAttribute`, ama `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a>AllowMultiple özelliği  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Özelliği, birden çok örneğini özniteliğinizi bir öğede mevcut olup olmadığını belirtir. Varsa kümesine **true**, birden çok örneği; izin verilir kümesine **false** (varsayılan), yalnızca bir örneğine izin verilir.  
  
 Aşağıdaki örnekte, `MyAttribute` varsayılan sahip <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerini **false**, sırada `YourAttribute` değerine sahip **doğru**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Bu öznitelikler birden çok örneğini uygulandığında `MyAttribute` derleyici hatası oluşturur. Aşağıdaki kod örneğinde geçerli kullanımı gösterilmiştir `YourAttribute` ve geçersiz kullanımı `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Her iki <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği ve <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği ayarlanmış **doğru**, başka bir sınıftan devralınan bir sınıf bir öznitelik devralır ve başka bir örneği aynı alt sınıfta uygulanan aynı özniteliğe sahip. Varsa <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ayarlanır **yanlış**, üst sınıfında herhangi bir öznitelik değerleri yeni alt sınıf içinde aynı öznitelik örneklerini üzerine yazılır.  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a>Öznitelik sınıfı bildirme  
 Uygulandıktan sonra <xref:System.AttributeUsageAttribute>, özniteliğinizi özelliklerini tanımlamak başlayabilirsiniz. Bir öznitelik sınıfı bildirimi aşağıdaki kodda gösterildiği gibi geleneksel bir sınıf bildirimine benzer.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Bu öznitelik tanımı aşağıdaki noktaları gösterilmektedir:  
  
-   Öznitelik sınıfları ortak sınıfları olarak bildirilmesi gerekir.  
  
-   Kurala göre öznitelik sınıfı adını bitip sözcüğüyle **özniteliği**. Gerekli olmasa da, bu kural okunabilirlik için önerilir. Öznitelik uygulandığında, öznitelik word'ün eklenmesi isteğe bağlıdır.  
  
-   Tüm öznitelik sınıfları öğesinden devralmalıdır doğrudan veya dolaylı olarak **System.Attribute'un**.  
  
-   Microsoft Visual Basic'te, tüm özel öznitelik sınıfları olmalıdır **AttributeUsageAttribute** özniteliği.  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a>Oluşturucuları bildirme  
 Öznitelikleri oluşturucular ile aynı şekilde geleneksel sınıflar olarak başlatılır. Aşağıdaki kod parçası, tipik öznitelik oluşturucunun gösterilmektedir. Bu ortak oluşturucu bir parametre alır ve bir üye değişkenine eşittir değerini ayarlar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Farklı değerleri birleşimlerini uyum sağlayacak şekilde Oluşturucusu aşırı yüklenebilir. Ayrıca tanımlarsanız bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) , özel öznitelik sınıfı için adlandırılmış ve konumsal parametreler birleşimi öznitelik başlatırken kullanabilirsiniz. Genellikle, gerekli tüm parametreleri olarak konumsal ve tüm isteğe bağlı parametreler olarak adlandırılan tanımlarsınız. Bu durumda, öznitelik gerekli parametresi olmadan başlatılamaz. Diğer tüm parametreler isteğe bağlıdır. Visual Basic'te bir ParamArray bağımsız değişkeni oluşturucuları öznitelik sınıfı için kullanmamalıdır unutmayın.  
  
 Aşağıdaki kod örneğinde, önceki Oluşturucusu isteğe bağlıdır ve gerekli parametreleri kullanılarak uygulanabilir kullanan bir öznitelik nasıl gösterir. Bu öznitelik gerekli bir Boole değeri ve isteğe bağlı bir dize özelliği olduğunu varsayar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a>Özellikleri bildirme  
 Adlandırılmış bir parametre tanımlayın veya özniteliği tarafından depolanan değer döndürmek için kolay bir yol sağlamak için bildirmek istiyorsanız, bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Öznitelik özellikleri döndürülecek veri türünün açıklaması ile genel varlıklar olarak bildirilmelidir. Özelliğin değerini tutun ve bu ilişkilendirmeyi değişkeni tanımlamanız **almak** ve **ayarlamak** yöntemleri. Aşağıdaki kod örneği, basit bir özellik, özniteliğinde uygulamak gösterilmiştir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a>Özel öznitelik örneği  
 Bu bölümde, önceki bilgileri bir araya getirir ve kod bölümünün Yazar hakkında bilgi belgeleri basit bir öznitelik tasarlamak nasıl gösterir. Bu örnekte öznitelik Programcı düzeyini ve adını depolar ve kod olup olmadığını gözden. Üç özel değişkenleri kaydetmek için gerçek değerlerini depolamak için kullanır. Her bir değişken alır ve değerlerini ayarlayan ortak bir özelliği tarafından gösterilir. Son olarak, Oluşturucusu iki gerekli parametre ile tanımlanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Tam adını kullanarak bu öznitelik uygulayabilirsiniz `DeveloperAttribute`, veya kısa ad kullanarak `Developer`, aşağıdaki yollardan biriyle.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 İlk örnek ile yalnızca gerekli hem gerekli ve isteğe bağlı parametreleri ile uygulanan öznitelik gösterirken, ikinci örnek adlandırılmış parametreleri, uygulanan öznitelik gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [Öznitelikler](../../../docs/standard/attributes/index.md)
