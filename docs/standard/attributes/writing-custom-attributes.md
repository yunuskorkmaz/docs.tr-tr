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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114d24c1fc523d5501deb4aa17f9541c5a918276
ms.sourcegitcommit: 7fe772c6c05a982153655d618c826e9839d39cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2018
ms.locfileid: "33574653"
---
# <a name="writing-custom-attributes"></a>Özel Öznitelikler Yazma
Kendi özel öznitelikler tasarlamak için çok sayıda yeni kavramları ana gerekmez. Nesne odaklı programlama ile ilgili bilgi sahibi olduğunuz ve sınıfları tasarlama ne yapılacağını bildiğiniz, ihtiyacınız olan bilgileri çoğunu zaten vardır. Özel öznitelikler sınıflardır doğrudan veya dolaylı olarak türetilen temelde geleneksel <xref:System.Attribute?displayProperty=nameWithType>. Yalnızca geleneksel sınıflar gibi özel öznitelikler, veri depolama ve alma yöntemler içerir.  
  
 Özel öznitelik sınıfları düzgün bir şekilde tasarlamak için birincil adımlar aşağıdaki gibidir:  
  
- [AttributeUsageAttribute uygulanıyor](#applying-the-attributeusageattribute)  
  
- [Öznitelik sınıf bildirme](#declaring-the-attribute-class)  
  
- [Oluşturucuları bildirme](#declaring-constructors)  
  
- [Özellikleri bildirme](#declaring-properties)  
  
 Bu bölümde, bu adımların her biri açıklar ve ile sonucuna bir [özel öznitelik örnek](#custom-attribute-example).  
  
## <a name="applying-the-attributeusageattribute"></a>AttributeUsageAttribute uygulanıyor  
 Bir özel özniteliği bildirimi ile başlayan <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, bazı önemli özelliklerinden biri, öznitelik sınıfı tanımlayan. Örneğin, öznitelik diğer sınıfları tarafından miras veya öznitelik uygulanabilir hangi elementleri belirtebilirsiniz. Aşağıdaki kod parçası nasıl kullanılacağını gösteren <xref:System.AttributeUsageAttribute>.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <xref:System.AttributeUsageAttribute> Özel öznitelikler oluşturmak için önemli olan üç üye vardır: [AttributeTargets](#attributetargets-member), [devralınan](#inherited-property), ve [AttributeUsage](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>AttributeTargets üyesi  
 Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> , bu öznitelik tüm program öğelerine uygulanabilir belirten belirtilir. Alternatif olarak, belirtebilirsiniz <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, gösteren, özniteliği yalnızca bir sınıfa uygulanabilir veya <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, gösteren, özniteliği yalnızca bir yöntem için uygulanabilir. Tüm program öğelerinin açıklaması için bu şekilde özel bir öznitelik tarafından işaretlenebilir.  
  
 Ayrıca birden çok geçirebilirsiniz <xref:System.AttributeTargets> değerleri. Aşağıdaki kod parçası, özel bir öznitelik herhangi bir sınıf veya yöntemi uygulanabilir belirtir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Devralınan özellik  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özelliği, öznitelik, öznitelik uygulandığı sınıflarından türetilen sınıflar tarafından devralınıp alınmayacağını belirtir. Bu özellik ya da gereken bir `true` (varsayılan) veya `false` bayrağı. Aşağıdaki örnekte, `MyAttribute` bir varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değerini `true`, ancak `YourAttribute` sahip bir <xref:System.AttributeUsageAttribute.Inherited%2A> değerini `false`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 İki öznitelikleri sonra bir yöntem temel sınıfta uygulanır `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Son olarak, sınıf `YourClass` temel sınıftan devralınan `MyClass`. Yöntem `MyMethod` gösterir `MyAttribute`, ama `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple özelliği  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Özelliği, öznitelik birden fazla örneğini bir öğe üzerinde mevcut olup olmadığını gösterir. Varsa kümesine `true`, birden çok örneği; kodlanabilmesi kümesine `false` (varsayılan), yalnızca bir örneğine izin verilir.  
  
 Aşağıdaki örnekte, `MyAttribute` bir varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerini `false`, ancak `YourAttribute` değeri `true`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Bu öznitelikler birden çok örneğini uygulandığında, `MyAttribute` bir derleyici hatası oluşturur. Aşağıdaki kod örneği geçerli kullanımını gösterir `YourAttribute` ve geçersiz kullanımı `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Her iki <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği ve <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği ayarlandığında `true`, başka bir sınıftan devralınan bir sınıf özniteliği devralır ve başka bir örneğinin aynı alt sınıf içinde uygulanan aynı özniteliğe sahip. Varsa <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ayarlanır `false`, üst sınıftaki herhangi bir öznitelik değerleri, aynı öznitelik, alt sınıfın yeni örneklerini tarafından üzerine yazılır.  
  
## <a name="declaring-the-attribute-class"></a>Öznitelik sınıf bildirme  
 Uygulandıktan sonra <xref:System.AttributeUsageAttribute>, özniteliğinizi özelliklerini tanımlamak başlayabilirsiniz. Öznitelik sınıfı bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıf bildirimine gibi görünür.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Bu öznitelik tanımı aşağıdaki noktaları göstermektedir:  
  
- Öznitelik sınıfları, genel sınıf olarak bildirilmelidir.  
  
- Kural gereği, öznitelik sınıfı adını word ile sona erer **özniteliği**. Gerekli olmasa da, bu kuralı okunabilirlik açısından önerilir. Öznitelik uygulandığında, eklenmesi, öznitelik sözcüğünü isteğe bağlıdır.  
  
- Tüm öznitelik sınıfları doğrudan veya dolaylı olarak devralmalıdır <xref:System.Attribute?displayProperty=nameWithType>.  
  
- Microsoft Visual Basic'te, tüm özel öznitelik sınıfları olmalıdır <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> özniteliği.  
  
## <a name="declaring-constructors"></a>Oluşturucuları bildirme  
 Öznitelikleri oluşturucularla geleneksel sınıflar olarak aynı şekilde başlatılır. Aşağıdaki kod parçası, tipik öznitelik oluşturucusunda gösterilmektedir. Bu ortak oluşturucu, bir parametre alır ve bir üye değişkeni değerine eşit olarak ayarlar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Değer farklı birleşimleri uyum sağlamak için oluşturucu aşırı yüklenebilir. Ayrıca tanımlarsanız bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) özel öznitelik sınıfınız için bir adlandırılmış ve konumsal parametreler birleşimi öznitelik başlatılırken kullanabilirsiniz. Genellikle, gerekli tüm parametreleri konumsal ve tüm isteğe bağlı parametreleri olarak adlandırılan tanımlarsınız. Bu durumda, öznitelik gerekli parametresi olmadan başlatılamaz. Diğer tüm parametreler isteğe bağlıdır. Visual Basic'te bir ParamArray bağımsız değişkeni bir öznitelik sınıfı için oluşturucular kullanmamalısınız unutmayın.  
  
 Aşağıdaki kod örneği, önceki Oluşturucusu isteğe bağlıdır ve gerekli parametreleri kullanarak uygulanabilir kullanan bir öznitelik nasıl gösterir. Bu öznitelik gerekli bir Boole değeri ve isteğe bağlı bir dize özelliği olduğu varsayılır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Özellikleri bildirme  
 İsterseniz adlandırılmış bir parametre tanımlayın veya, özniteliği tarafından depolanan değer döndürmek için kolay bir yol sağlar, bildirmek bir [özelliği](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Öznitelik özellikleri ile döndürülecek veri türünün açıklaması genel varlıklar olarak bildirilmelidir. Özelliğin değerini tutun ve ilişkilendirin değişkeni tanımlamanız **alma** ve **ayarlamak** yöntemleri. Aşağıdaki kod örneği, özniteliğinde basit bir özelliğin uygulanması gösterilmektedir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Özel öznitelik örneği  
 Bu bölümde, önceki bilgileri içerir ve kodun bir bölümünü Yazar hakkında bilgi belgeleri, basit bir öznitelik tasarlama işlemi gösterilmektedir. Bu örnekte öznitelik Programcı düzeyini ve adını depolar ve kod olup olmadığını gözden geçirildi. Üç özel değişkenlere kaydetmek için gerçek değerleri depolamak için kullanır. Her bir değişken alır ve ayarlar ortak bir özelliği tarafından temsil edilir. Son olarak, Oluşturucu iki gerekli parametreler ile tanımlanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Bu öznitelik tam adı kullanılarak uygulayabilirsiniz `DeveloperAttribute`, ya da kısa ad kullanarak `Developer`, aşağıdaki yollardan biriyle.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 İlk örnekte, yalnızca gerekli parametreler, hem gerekli ve isteğe bağlı parametrelerle uygulanan öznitelik gösterirken, ikinci örnek adlı ile uygulanan öznitelik gösterilmektedir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>  
 [Öznitelikler](../../../docs/standard/attributes/index.md)
