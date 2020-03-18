---
title: Özel Öznitelikler Yazma
ms.date: 07/17/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140578"
---
# <a name="writing-custom-attributes"></a>Özel Öznitelikler Yazma
Kendi özel özniteliklerinizi tasarlamak için birçok yeni kavramda ustalaşmanız gerekmez. Nesne yönelimli programlamaya aşinaysanız ve sınıfları nasıl tasarladığınızı biliyorsanız, zaten gereken bilginin çoğuna sahipsiniz. Özel öznitelikler, temelde doğrudan veya dolaylı olarak <xref:System.Attribute?displayProperty=nameWithType>türeyen geleneksel sınıflardır. Geleneksel sınıflar gibi, özel öznitelikler de verileri depolayan ve alınan yöntemler içerir.  
  
 Özel öznitelik sınıflarını düzgün bir şekilde tasarlamak için birincil adımlar aşağıdaki gibidir:  
  
- [ÖznitelikUygulamaKullanımAttribute](#applying-the-attributeusageattribute)  
  
- [Öznitelik sınıfını bildirme](#declaring-the-attribute-class)  
  
- [Yapıcıları bildirme](#declaring-constructors)  
  
- [Özellikleri bildirme](#declaring-properties)  
  
 Bu bölümde bu adımların her biri açıklanır ve özel bir [öznitelik örneği](#custom-attribute-example)ile sona erer.  
  
## <a name="applying-the-attributeusageattribute"></a>ÖznitelikUygulamaKullanımAttribute  
 Özel öznitelik <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>bildirimi, öznitelik sınıfınızın bazı temel özelliklerini tanımlayan , ile başlar. Örneğin, özniteliğinizin diğer sınıflar tarafından devralınıp alınamayacağını veya özniteliğin hangi öğelere uygulanabileceğini belirtebilirsiniz. Aşağıdaki kod <xref:System.AttributeUsageAttribute>parçası.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 Özel <xref:System.AttributeUsageAttribute> özniteliklerin oluşturulması için önemli olan üç üyesi vardır: [AttributeTargets](#attributetargets-member), [Devralınan](#inherited-property)ve [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>ÖznitelikHedef Üye  
 Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir. Alternatif olarak, <xref:System.AttributeTargets.Class?displayProperty=nameWithType>özniteliğinizin yalnızca bir sınıfa uygulanabileceğini belirten <xref:System.AttributeTargets.Method?displayProperty=nameWithType>veya özniteliğinizin yalnızca bir yönteme uygulanabileceğini belirten bir belirtebilirsiniz. Tüm program öğeleri bu şekilde özel bir öznitelik ile açıklama için işaretlenebilir.  
  
 Ayrıca birden çok <xref:System.AttributeTargets> değer geçirebilirsiniz. Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntem uygulanabilir belirtir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Devralınan Özellik  
 Özellik, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özniteliğinizin uygulandığı sınıflardan türetilen sınıflar tarafından devralınıp alınamayacağını gösterir. Bu özellik bir `true` (varsayılan) `false` veya bayrak alır. Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değeri `true`, `YourAttribute` . <xref:System.AttributeUsageAttribute.Inherited%2A> `false`  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 İki öznitelik daha sonra taban sınıftabir `MyClass`yönteme uygulanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Son olarak, `YourClass` sınıf taban sınıftan `MyClass`devralır. Yöntem, `MyMethod` `MyAttribute`ancak gösterir `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>Birden Fazla Özelliğe İzin Verme  
 Özellik, <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> özniteliğinizin birden çok örneğinin bir öğeüzerinde var olup olmadığını gösterir. `true`Ayarlanmışsa , birden çok örneğine izin verilir; `false` (varsayılan) olarak ayarlanmışsa, yalnızca bir örneğine izin verilir.  
  
 Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değeri `false`, `YourAttribute` `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Bu özniteliklerin birden çok `MyAttribute` örneği uygulandığında, derleyici hatası üretir. Aşağıdaki kod örneği geçerli kullanımını `YourAttribute` ve `MyAttribute`geçersiz kullanımını gösterir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Hem <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özellik hem <xref:System.AttributeUsageAttribute.Inherited%2A> de özellik `true`ayarlanmışsa, başka bir sınıftan devralınan bir sınıf bir öznitelik devralabilir ve aynı alt sınıfta uygulanan aynı öznitelik başka bir örneği olabilir. <xref:System.AttributeUsageAttribute.AllowMultiple%2A> Ayarlanırsa, üst sınıftaki özniteliklerin değerleri alt sınıfta ki aynı özniteliğe sahip yeni örneklertarafından üzerine `false`yazılır.  
  
## <a name="declaring-the-attribute-class"></a>Öznitelik Sınıfını Bildirme  
 <xref:System.AttributeUsageAttribute>Uyguladıktan sonra, özniteliğinizin özelliklerini tanımlamaya başlayabilirsiniz. Bir öznitelik sınıfının bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıfın bildirimine benzer.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Bu öznitelik tanımı aşağıdaki noktaları gösterir:  
  
- Öznitelik sınıfları ortak sınıflar olarak bildirilmelidir.  
  
- Öznitelik sınıfının adı, öznitelik sınıfının adı **Öznitelik**sözcüğüyle sona erer. Gerekli olmasa da, bu sözleşme okunabilirlik için tavsiye edilir. Öznitelik uygulandığında, Öznitelik sözcüğünün eklenmesi isteğe bağlıdır.  
  
- Tüm öznitelik sınıfları doğrudan veya <xref:System.Attribute?displayProperty=nameWithType>dolaylı olarak devralınmalıdır.  
  
- Microsoft Visual Basic'te, tüm özel <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> öznitelik sınıfları özniteliğe sahip olmalıdır.  
  
## <a name="declaring-constructors"></a>Yapıcıları Bildirme  
 Öznitelikler, geleneksel sınıflarla aynı şekilde oluşturucularla başharfe alınır. Aşağıdaki kod parçası tipik bir öznitelik oluşturucu gösterir. Bu ortak oluşturucu bir parametre alır ve değerine eşit bir üye değişken ayarlar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Farklı değer kombinasyonlarını karşılamak için oluşturucuyu aşırı yükleyebilirsiniz. Özel öznitelik sınıfınız için bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) de tanımlarsanız, özniteliği başolarak alırken adlandırılmış ve konumsal parametrelerin bir birleşimini kullanabilirsiniz. Genellikle, gerekli tüm parametreleri konumsal olarak ve tüm isteğe bağlı parametreleri adlandırılmış olarak tanımlarsınız. Bu durumda, öznitelik gerekli parametre olmadan başharfolamaz. Diğer tüm parametreler isteğe bağlıdır. Visual Basic'te, öznitelik sınıfı nın oluşturucularının ParamArray bağımsız değişkeni kullanmaması gerektiğini unutmayın.  
  
 Aşağıdaki kod örneği, önceki oluşturucuyu kullanan bir özniteliğin isteğe bağlı ve gerekli parametreler kullanılarak nasıl uygulanabileceğini gösterir. Bu öznitelik bir gerekli Boolean değeri ve bir isteğe bağlı dize özelliği olduğunu varsayar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Özellikleri Bildirme  
 Adlandırılmış bir parametre tanımlamak veya özniteliğiniz tarafından depolanan değerleri döndürmek için kolay bir yol sağlamak istiyorsanız, bir [özellik](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))bildirin. Öznitelik özellikleri, döndürülecek veri türünün açıklamasıyla birlikte kamu tüzel kişileri olarak beyan edilmelidir. Mülkünüzün değerini tutacak değişkeni tanımlayın ve **get** ve **set** yöntemleriyle ilişkilendirin. Aşağıdaki kod örneği, özniteliğinizde basit bir özelliğin nasıl uygulanacağını gösterir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Özel Öznitelik Örneği  
 Bu bölümde önceki bilgiler içerir ve kod bir bölümünün yazarı hakkında bilgi belgeler basit bir öznitelik nasıl tasarlanır gösterir. Bu örnekteki öznitelik, programcının adını ve düzeyini ve kodun gözden geçirilip geçirilemediğini depolar. Kaydetmek için gerçek değerleri depolamak için üç özel değişken kullanır. Her değişken, değerleri alan ve ayarlayan bir kamu malı tarafından temsil edilir. Son olarak, yapıcı iki gerekli parametreleri ile tanımlanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Bu özniteliği tam adı `DeveloperAttribute`kullanarak veya kısaltılmış adı `Developer`kullanarak aşağıdaki yollardan biriyle uygulayabilirsiniz.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 İlk örnek, yalnızca gerekli adlandırılmış parametrelerle uygulanan özniteliği gösterirken, ikinci örnek hem gerekli hem de isteğe bağlı parametrelerle uygulanan özniteliği gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Öznitelikler](../../../docs/standard/attributes/index.md)
