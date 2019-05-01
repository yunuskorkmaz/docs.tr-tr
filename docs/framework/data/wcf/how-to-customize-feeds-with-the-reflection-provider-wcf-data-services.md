---
title: 'Nasıl yapılır: (WCF Veri Hizmetleri) yansıma sağlayıcısı ile akışları özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: f09c9827498dfd6b85a8476e824d06bfb481d1f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876557"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: (WCF Veri Hizmetleri) yansıma sağlayıcısı ile akışları özelleştirme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlığın özelliklerini AtomPub protokolünde tanımlanan kullanılmayan öğelere eşlenebilir böylece bir veri hizmeti yanıttaki Atom serileştirme özelleştirmenize olanak sağlar. Bu konuda, yansıma sağlayıcısını kullanarak tarafından tanımlanan bir veri modeli varlık türleri için eşleme öznitelikleri tanımlamak gösterilmektedir. Daha fazla bilgi için [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Bu örnek için veri modeli konusunda tanımlanan [nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, her iki özelliklerini `Order` türü mevcut Atom öğeleri eşlendi. `Product` Özelliği `Item` türü ayrı bir ad alanı özel bir akış öznitelikte eşlenmiş durumda.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI'sini aşağıdaki sonucu verir `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
