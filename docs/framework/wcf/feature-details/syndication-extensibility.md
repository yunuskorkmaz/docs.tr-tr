---
title: Dağıtım Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 226ea682d8b17a818e6d5be2097a19315d106bda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170813"
---
# <a name="syndication-extensibility"></a>Dağıtım Genişletilebilirliği
Dağıtım API dağıtılmış içeriği, çeşitli biçimlerde hat yazılmasına izin veren bir biçim nötr programlama modeli sağlamak için tasarlanmıştır. Aşağıdaki sınıflar soyut bir veri modeli oluşur:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Bazı adları farklı olmasına rağmen bu sınıfların Atom 1.0 belirtiminde tanımlanan yapıları yakından eşlenir.  
  
 Bir anahtar dağıtım protokolleri genişletilebilirlik özelliğidir. Atom 1.0 hem de RSS 2.0 ekleyin öznitelikler ve öğeler'de tanımlanmayan, dağıtım akışlarını. Windows Communication Foundation (WCF) dağıtım programlama modeli, özel öznitelikler ve uzantıları, geniş yazılmış erişim ile çalışma ve yeni bir sınıf türetmek aşağıdaki yöntemler sağlar.  
  
## <a name="loosely-typed-access"></a>Gevşek yazılmış erişim  
 Yeni bir sınıf türetilerek uzantılar ekleme, ek kod yazılmasını gerektirir. Başka bir seçenek uzantıları geniş yazılmış şekilde erişir. Adlı özellikleri sendikasyonu soyut veri modelinde tanımlanan türleri içerir `AttributeExtensions` ve `ElementExtensions` (bir özel durum ile <xref:System.ServiceModel.Syndication.SyndicationContent> sahip bir `AttributeExtensions` özelliği ancak Hayır `ElementExtensions` özelliği). Bu özellikler tarafından işlenmemiş uzantıları koleksiyonlarıdır `TryParseAttribute` ve `TryParseElement` yöntemlerini sırasıyla. İşlenmemiş uzantılara çağırarak erişebileceğiniz <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> üzerinde `ElementExtensions` özelliği <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, ve <xref:System.ServiceModel.Syndication.SyndicationCategory>. Bu yöntem kümesi belirtilen ad ve ad alanı ile tüm uzantıları bulur, bunları tek tek örneğine çıkarır `TExtension` ve bir koleksiyonu olarak döndürür `TExtension` nesneleri.  
  
## <a name="deriving-a-new-class"></a>Yeni sınıf türetme  
 Mevcut soyut veri modeli sınıfların herhangi yeni bir sınıf türetebilirsiniz. Çalıştığınız akışları çoğu belirli bir uzantısı olan bir uygulama uygularken bunu. Bu konu başlığında, programın çalıştığı akışları çoğunu içeren bir `MyExtension` uzantısı. Geliştirilmiş bir programlama deneyimi sağlamak için aşağıdaki adımları uygulayın:  
  
-   Uzantı verileri tutmak için bir sınıf oluşturun. Bu durumda, MyExtension adlı bir sınıf oluşturun.  
  
-   Gelen MyExtensionItem adlı bir sınıf türetin <xref:System.ServiceModel.Syndication.SyndicationItem> amaçlar programlanabilme MyExtension türünün bir özelliği kullanıma sunmak için.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> MyExtensionItem sınıfındaki bir MyExtension okunduğunda yeni bir MyExtension örneği oluşturmak için.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> MyExtensionItem sınıfında MyExtension özelliğinin içeriği yazmak için bir XML yazıcısı.  
  
-   Gelen MyExtensionFeed adlı bir sınıf türetin <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Geçersiz kılma <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> varsayılan yerine bir MyExtensionItem örneklemek için MyExtensionFeed sınıfında <xref:System.ServiceModel.Syndication.SyndicationItem>. Bir dizi yöntem tanımlanmış <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> oluşturabilir, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, ve <xref:System.ServiceModel.Syndication.SyndicationPerson> nesneleri (örneğin, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, ve <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Her biri, özel olarak türetilmiş bir sınıf oluşturmak için kılınabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Dağıtım Mimarisi](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
