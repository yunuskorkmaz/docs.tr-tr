---
title: Dağıtım Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 5e8f47b45897f46e15847c793c986e953523e66b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600730"
---
# <a name="syndication-extensibility"></a>Dağıtım Genişletilebilirliği
Dağıtım API 'SI, dağıtılmış içeriğin çeşitli biçimlerde bir hatta yazılmasına izin veren biçim nötr bir programlama modeli sağlamak üzere tasarlanmıştır. Soyut veri modeli aşağıdaki sınıflardan oluşur:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Bu sınıflar, bazı adların farklı olmasına rağmen Atom 1,0 belirtiminde tanımlanan yapılara yakın şekilde eşlenir.  
  
 Dağıtım protokollerinin temel bir özelliği genişletilebilirlik ' dir. Hem Atom 1,0 hem de RSS 2,0, belirtimlerde tanımlanmayan dağıtım akışlarına öznitelikler ve öğeler ekleyin. Windows Communication Foundation (WCF) dağıtım programlama modeli, özel öznitelikler ve uzantılarla, gevşek olarak yazılmış erişimle ve yeni bir sınıf türetmede aşağıdaki yolları sağlar.  
  
## <a name="loosely-typed-access"></a>Gevşek olarak yazılmış erişim  
 Yeni bir sınıf türeterek uzantıları eklemek için ek kod yazılması gerekir. Başka bir seçenek, uzantılara, gevşek olarak yazılmış bir şekilde erişiyor. Dağıtım soyut veri modelinde tanımlanan tüm türler, `AttributeExtensions` ve `ElementExtensions` (bir özel durum dışında, özelliği olan, <xref:System.ServiceModel.Syndication.SyndicationContent> `AttributeExtensions` ancak `ElementExtensions` özelliği olmayan) özellikler içerir. Bu özellikler, ve yöntemleri tarafından işlenmediği uzantıların koleksiyonlarıdır `TryParseAttribute` `TryParseElement` . ,,, Ve özelliğini çağırarak, bu işlenmemiş uzantılara erişebilirsiniz <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> `ElementExtensions` <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> <xref:System.ServiceModel.Syndication.SyndicationLink> <xref:System.ServiceModel.Syndication.SyndicationPerson> <xref:System.ServiceModel.Syndication.SyndicationCategory> . Bu yöntem kümesi, belirtilen ad ve ad alanına sahip tüm uzantıları bulur, bunları bağımsız olarak bir dizi örneğine ayırır `TExtension` ve bunları bir nesne koleksiyonu olarak döndürür `TExtension` .  
  
## <a name="deriving-a-new-class"></a>Yeni bir sınıf türetiliyor  
 Mevcut soyut veri modeli sınıflarından herhangi birinden yeni bir sınıf türetebilirsiniz. Üzerinde çalıştığınız akışların çoğunun belirli bir uzantıya sahip olduğu bir uygulamayı uygularken bunu yapın. Bu konuda, programın birlikte kullandığı akışların çoğu bir `MyExtension` uzantı içerir. Gelişmiş bir programlama deneyimi sağlamak için aşağıdaki adımları uygulayın:  
  
- Uzantı verilerini tutacak bir sınıf oluşturun. Bu durumda, MyExtension adlı bir sınıf oluşturun.  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>Programlama amacıyla MyExtension türünde bir özelliği göstermek Için MyExtensionItem adlı bir sınıf türetirsiniz.  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29>MyExtensionItem sınıfında, MyExtension içinde okunan yeni bir MyExtension örneği oluşturmak için geçersiz kılın.  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29>MyExtension özelliğinin içeriğini BIR XML yazıcısına yazmak Için MyExtensionItem sınıfında geçersiz kılın.  
  
- Öğesinden MyExtensionFeed adlı bir sınıf türet <xref:System.ServiceModel.Syndication.SyndicationFeed> .  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem>MyExtensionFeed sınıfında, varsayılan yerine bir MyExtensionItem örneği oluşturmak için geçersiz kılın <xref:System.ServiceModel.Syndication.SyndicationItem> . <xref:System.ServiceModel.Syndication.SyndicationFeed>Ve içinde <xref:System.ServiceModel.Syndication.SyndicationItem> ,, <xref:System.ServiceModel.Syndication.SyndicationLink> <xref:System.ServiceModel.Syndication.SyndicationCategory> ve <xref:System.ServiceModel.Syndication.SyndicationPerson> nesneleri (örneğin,,, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink> <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory> ve <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson> ) oluşturabileceğiniz bir dizi Yöntem tanımlanmıştır. Özel bir türetilmiş sınıf oluşturmak için tümünün geçersiz kılınabilen.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Dağıtımı Genel Bakış](wcf-syndication-overview.md)
- [Dağıtım Mimarisi](architecture-of-syndication.md)
