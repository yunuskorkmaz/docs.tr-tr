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
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="407ae-102">Nasıl yapılır: (WCF Veri Hizmetleri) yansıma sağlayıcısı ile akışları özelleştirme</span><span class="sxs-lookup"><span data-stu-id="407ae-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="407ae-103">bir varlığın özelliklerini AtomPub protokolünde tanımlanan kullanılmayan öğelere eşlenebilir böylece bir veri hizmeti yanıttaki Atom serileştirme özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="407ae-103">enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="407ae-104">Bu konuda, yansıma sağlayıcısını kullanarak tarafından tanımlanan bir veri modeli varlık türleri için eşleme öznitelikleri tanımlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="407ae-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="407ae-105">Daha fazla bilgi için [akış özelleştirme](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="407ae-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="407ae-106">Bu örnek için veri modeli konusunda tanımlanan [nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="407ae-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="407ae-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="407ae-107">Example</span></span>  
 <span data-ttu-id="407ae-108">Aşağıdaki örnekte, her iki özelliklerini `Order` türü mevcut Atom öğeleri eşlendi.</span><span class="sxs-lookup"><span data-stu-id="407ae-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="407ae-109">`Product` Özelliği `Item` türü ayrı bir ad alanı özel bir akış öznitelikte eşlenmiş durumda.</span><span class="sxs-lookup"><span data-stu-id="407ae-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="407ae-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="407ae-110">Example</span></span>  
 <span data-ttu-id="407ae-111">Önceki örnekte URI'sini aşağıdaki sonucu verir `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="407ae-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="407ae-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="407ae-112">See also</span></span>

- [<span data-ttu-id="407ae-113">Yansıma Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="407ae-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
