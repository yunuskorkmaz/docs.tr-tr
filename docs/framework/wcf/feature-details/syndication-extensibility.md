---
title: "Dağıtım Genişletilebilirliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5322ff2c79ab5051b3a9aaaeaafe7db6c9c2f683
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="syndication-extensibility"></a>Dağıtım Genişletilebilirliği
Dağıtım API, çeşitli biçimlerde hat yazılması dağıtılmış içerik sağlayan bir biçim Tarafsız programlama modeli sağlamak için tasarlanmıştır. Soyut veri modeli şu sınıflardan oluşur:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Adlarından bazıları farklı olmasına rağmen bu sınıfların Atom 1.0 belirtiminde tanımlanan yapıları yakından eşlenir.  
  
 Bir anahtar dağıtım protokolleri genişletilebilirlik özelliğidir. Atom 1.0 ve RSS 2.0 eklemeniz öznitelikler ve öğeler belirtimleri tanımlanmamış dağıtım akışlarını. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Dağıtım programlama modeli özel özniteliklere ve uzantıları, geniş yazılmış erişim ile çalışma ve yeni bir sınıf türetme aşağıdaki yollardan sağlar.  
  
## <a name="loosely-typed-access"></a>Gevşek yazılmış erişim  
 Yeni bir sınıf türetme tarafından uzantılar ekleme ek kod yazma gerektirir. Başka bir seçenek uzantıları geniş yazılmış bir yolla erişiyor. Tüm dağıtım soyut veri modelinde tanımlanan türleri adlı özelliklerini içeren `AttributeExtensions` ve `ElementExtensions` (bir durumla <xref:System.ServiceModel.Syndication.SyndicationContent> sahip bir `AttributeExtensions` özelliği ancak hiçbir `ElementExtensions` özelliği). Bu özellikler tarafından işlenmemiş uzantıları koleksiyonlarıdır `TryParseAttribute` ve `TryParseElement` yöntemleri sırasıyla. İşlenmemiş uzantılara çağırarak erişebilirsiniz <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> üzerinde `ElementExtensions` özelliği <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, ve <xref:System.ServiceModel.Syndication.SyndicationCategory>. Bu yöntemler kümesi belirtilen ve ad alanına sahip tüm uzantıları bulur, bunları tek tek örneklerini seri durumdan çıkarır `TExtension` ve koleksiyonu olarak döndürür `TExtension` nesneleri.  
  
## <a name="deriving-a-new-class"></a>Yeni bir sınıf türetme  
 Yeni bir sınıf herhangi bir varolan soyut veri modeli sınıfı türetilemeyeceğini. Bunu, birlikte çalıştığınız akışları çoğunu belirli bir uzantıya sahip bir uygulama uygularken yapın. Bu konuda, program çalışır akışları çoğunu içeren bir `MyExtension` uzantısı. Geliştirilmiş bir programlama deneyimi sunmak için aşağıdaki adımları uygulayın:  
  
-   Uzantısını verileri tutmak için bir sınıf oluşturun. Bu durumda, MyExtension adlı bir sınıf oluşturun.  
  
-   Gelen MyExtensionItem adlı bir sınıf türetin <xref:System.ServiceModel.Syndication.SyndicationItem> programlamasına amacıyla MyExtension türünde bir özellik kullanıma sunmak için.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> MyExtensionItem sınıfında içinde bir MyExtension okurken bir yeni MyExtension örneği.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> bir XML yazıcı MyExtension özelliği içeriğini yazmak için MyExtensionItem sınıfında.  
  
-   Gelen MyExtensionFeed adlı bir sınıf türetin <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> MyExtensionItem varsayılan yerine örneği oluşturmak için MyExtensionFeed sınıfında <xref:System.ServiceModel.Syndication.SyndicationItem>. Bir dizi yöntem tanımlanmış <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> , oluşturabilirsiniz <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, ve <xref:System.ServiceModel.Syndication.SyndicationPerson> nesneleri (örneğin, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, ve <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Her biri özel bir türetilmiş sınıf oluşturmak için geçersiz kılınabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Dağıtım Mimarisi](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
