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
ms.openlocfilehash: fb22e87569a8e243813b3186232b6989abeb2a5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161314"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Nasıl yapılır: yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, bir varlık özelliklerinin AtomPub protokolünde tanımlı kullanılmayan öğelerle eşlenilmesi için bir veri hizmeti yanıtında atom serileştirmesini özelleştirmenize olanak sağlar. Bu konu başlığı altında, yansıma sağlayıcısı kullanılarak tanımlanan bir veri modelinde varlık türleri için eşleme özniteliklerinin nasıl tanımlanacağı gösterilmektedir. Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).  
  
 Bu örneğe ilişkin veri modeli, [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md) konusunda tanımlanmıştır  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, türünün her iki özelliği de `Order` var olan atom öğelerine eşlenir. `Product`Türün özelliği, `Item` ayrı bir ad alanında özel bir akış özniteliğiyle eşleştirilir.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Örnek  

 Önceki örnekte URI için aşağıdaki sonuç döndürülür `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` .  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
