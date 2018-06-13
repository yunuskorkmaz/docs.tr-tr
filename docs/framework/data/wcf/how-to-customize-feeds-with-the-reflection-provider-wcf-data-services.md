---
title: 'Nasıl yapılır: yansıma sağlayıcısı (WCF Veri Hizmetleri) ile akışları özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 984a4aac43689be0ec80e7f6c289e8d5229e9e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358014"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısı (WCF Veri Hizmetleri) ile akışları özelleştirme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlığın özelliklerini AtomPub protokolünde tanımlanan kullanılmayan öğeleri eşlenebilir böylece bir veri hizmeti yanıtında Atom serileştirme özelleştirmenize olanak tanır. Bu konu, yansıma sağlayıcısı kullanılarak tanımlanmış bir veri modeli varlık türlerine eşleme öznitelikleri tanımlamak gösterilmiştir. Daha fazla bilgi için bkz: [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Bu örnek için veri modeli konusundaki tanımlanan [nasıl yapılır: yansıma sağlayıcı veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her iki özelliklerini `Order` türü mevcut Atom öğelerine eşlendi. `Product` Özelliği `Item` türü ayrı bir ad alanındaki özel bir akış özniteliği eşleştirilir.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI'sini aşağıdaki sonucu döndürür `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
