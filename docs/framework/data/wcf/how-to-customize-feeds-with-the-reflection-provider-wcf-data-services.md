---
title: 'Nasıl yapılır: Yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 43f46729ba84356bcb6507779bef9e4fd35bc315
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790680"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="f04fa-102">Nasıl yapılır: Yansıma sağlayıcısı ile akışları özelleştirme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="f04fa-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="f04fa-103">bir varlık özelliklerinin AtomPub protokolünde tanımlı kullanılmayan öğelerle eşlenilmesi için bir veri hizmeti yanıtında atom serileştirmesini özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f04fa-103">enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="f04fa-104">Bu konu başlığı altında, yansıma sağlayıcısı kullanılarak tanımlanan bir veri modelinde varlık türleri için eşleme özniteliklerinin nasıl tanımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f04fa-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="f04fa-105">Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f04fa-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="f04fa-106">Bu örneğe [ilişkin veri modeli, konusunda nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="f04fa-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f04fa-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f04fa-107">Example</span></span>  
 <span data-ttu-id="f04fa-108">Aşağıdaki örnekte, `Order` türünün her iki özelliği de var olan atom öğelerine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f04fa-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="f04fa-109">`Item` Türün özelliği, ayrı bir ad alanında özel bir akış özniteliğiyle eşleştirilir. `Product`</span><span class="sxs-lookup"><span data-stu-id="f04fa-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="f04fa-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f04fa-110">Example</span></span>  
 <span data-ttu-id="f04fa-111">Önceki örnekte URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`için aşağıdaki sonuç döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f04fa-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="f04fa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f04fa-112">See also</span></span>

- [<span data-ttu-id="f04fa-113">Yansıma Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f04fa-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
