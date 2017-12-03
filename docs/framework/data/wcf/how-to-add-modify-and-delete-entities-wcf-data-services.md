---
title: "Nasıl yapılır: ekleme, değiştirme ve silme varlıkları (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e41502fee9cfa272b154f6ddaf0e6a41a482bc7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>Nasıl yapılır: ekleme, değiştirme ve silme varlıkları (WCF Veri Hizmetleri)
İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplıkları, oluşturabilir, güncelleştirebilir ve nesnelerde eşdeğer eylemleri gerçekleştirerek bir veri hizmeti bulunan varlık verileri silme <xref:System.Data.Services.Client.DataServiceContext>. Daha fazla bilgi için bkz: [veri hizmeti güncelleştirme](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Bu konudaki örnek Northwind örnek veri hizmeti ve otomatik olarak oluşturulur istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve ardından çağırır <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> bağlamda öğesi oluşturmak için. Bir HTTP POST iletisi verileri gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alır ve var olan bir nesne değiştirir ve daha sonra çağırır <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> bağlam öğesinde güncelleştirilmiş olarak işaretlemek için. Bir HTTP birleştirme iletisi verileri gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> bağlamında öğe silindi olarak işaretlemek için. Bir HTTP DELETE iletisi verileri gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir nesne örneği oluşturur ve ardından çağırır <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> ilgili sipariş bağlantısını birlikte bağlamda öğesi oluşturmak için. Bir HTTP POST iletisi verileri gönderilir ne zaman hizmet <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> yöntemi çağrılır.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Nasıl yapılır: DataServiceContext var olan bir varlık ekleme](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)  
 [Nasıl yapılır: Varlık İlişkileri tanımlama](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)  
 [Toplu işlem](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
