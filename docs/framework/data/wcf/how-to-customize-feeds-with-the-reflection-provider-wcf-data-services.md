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
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="01c79-102">Nasıl yapılır: yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="01c79-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="01c79-103">WCF Veri Hizmetleri, bir varlık özelliklerinin AtomPub protokolünde tanımlı kullanılmayan öğelerle eşlenilmesi için bir veri hizmeti yanıtında atom serileştirmesini özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="01c79-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="01c79-104">Bu konu başlığı altında, yansıma sağlayıcısı kullanılarak tanımlanan bir veri modelinde varlık türleri için eşleme özniteliklerinin nasıl tanımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="01c79-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="01c79-105">Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="01c79-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="01c79-106">Bu örneğe ilişkin veri modeli, [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md) konusunda tanımlanmıştır</span><span class="sxs-lookup"><span data-stu-id="01c79-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c79-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="01c79-107">Example</span></span>  
 <span data-ttu-id="01c79-108">Aşağıdaki örnekte, `Order` türünün her iki özelliği de varolan atom öğelerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="01c79-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="01c79-109">`Item` türünün `Product` özelliği, ayrı bir ad alanında özel bir akış özniteliğiyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="01c79-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="01c79-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="01c79-110">Example</span></span>  
 <span data-ttu-id="01c79-111">Önceki örnekte URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`için aşağıdaki sonuç döndürülür.</span><span class="sxs-lookup"><span data-stu-id="01c79-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="01c79-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01c79-112">See also</span></span>

- [<span data-ttu-id="01c79-113">Yansıma Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="01c79-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
