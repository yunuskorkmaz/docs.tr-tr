---
title: 'Nasıl yapılır: yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: d3e2d587978a4c82784c8cfc8a7acc17cf601c3a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569141"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir varlık özelliklerinin AtomPub protokolünde tanımlı kullanılmayan öğelerle eşlenilmesi için bir veri hizmeti yanıtında atom serileştirmesini özelleştirmenize olanak sağlar. Bu konu başlığı altında, yansıma sağlayıcısı kullanılarak tanımlanan bir veri modelinde varlık türleri için eşleme özniteliklerinin nasıl tanımlanacağı gösterilmektedir. Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).  
  
 Bu örneğe ilişkin veri modeli, [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md) konusunda tanımlanmıştır  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Order` türünün her iki özelliği de varolan atom öğelerine eşlenir. `Item` türünün `Product` özelliği, ayrı bir ad alanında özel bir akış özniteliğiyle eşlenir.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`için aşağıdaki sonuç döndürülür.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
