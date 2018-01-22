---
title: "Nasıl yapılır: Entity Framework sağlayıcısı (WCF Veri Hizmetleri) ile akışları özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 276aea81716f58ed4a0d6ba8e1f8e2bcdbedb908
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Nasıl yapılır: Entity Framework sağlayıcısı (WCF Veri Hizmetleri) ile akışları özelleştirme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]bir varlığın özelliklerini AtomPub protokolünde tanımlanan kullanılmayan öğeleri eşlenebilir böylece bir veri hizmeti yanıtında Atom serileştirme özelleştirmenize olanak tanır. Bu konu, Entity Framework sağlayıcısı kullanarak bir .edmx dosyasında tanımlanan bir veri modeli varlık türlerine eşleme öznitelikleri tanımlamak gösterilmiştir. Daha fazla bilgi için bkz: [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Bu konuda veri modeli içeriyor aracı tarafından oluşturulan .edmx dosyasının el ile değiştirir. Veri modeli için Uzantılar Entity Designer tarafından desteklenmediği için dosyayı el ile değiştirmeniz gerekir. Varlık veri modeli araçları oluşturmak .edmx dosyasının hakkında daha fazla bilgi için bkz: [.edmx dosyasının genel bakış](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4). Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Akış özelleştirme öznitelikler eklemek için Northwind.edmx dosyasını el ile değiştirme  
  
1.  İçinde **Çözüm Gezgini**, sağ `Northwind.edmx` dosya ve ardından **birlikte Aç**.  
  
2.  İçinde **birlikte Aç - Northwind.edmx** iletişim kutusunda **XML Düzenleyicisi**ve ardından **Tamam**.  
  
3.  Bulun `ConceptualModels` öğesi ve varolan Değiştir `Customers` varlık türünü içeren öğesi ile akış özelleştirme eşleme öznitelikleri:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Değişiklikleri Northwind.edmx dosyasını kaydedip kapatın.  
  
5.  (İsteğe bağlı) Northwind.edmx dosyasını sağ tıklatın ve ardından **çalıştırmak özel araç**.  
  
     Gerekli nesne katmanı dosyası oluşturur.  
  
6.  Projeyi yeniden derleyin.  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI'sini aşağıdaki sonucu döndürür `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
