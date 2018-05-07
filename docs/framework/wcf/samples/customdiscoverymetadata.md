---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Bu örnek, bulma meta veri hizmeti tarafından sunulan bulunabilirlik bir uç nokta için özel XML meta verileri takın gösterilmektedir. Örnek sonra nasıl bir istemci hizmeti için arama yapın ve bu özel veri ayıklamak gösterir. Bu örnek iki proje, hizmet ve istemci oluşur.  
  
## <a name="service"></a>Hizmet  
 İçinde `main` yöntemi, örnek gösterilmektedir türünde bir nesne <xref:System.Xml.Linq.XElement> istenen alanları ile doldurulur ve eklenir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için özel bir uç nokta eklenir. Bu belirli uç bulunduğunda bulma meta verileri buraya eklenen özel verileri içerir.  
  
## <a name="client"></a>İstemci  
 Örnek gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> üzerinde çağrılan yöntemi bir <xref:System.ServiceModel.Discovery.DiscoveryClient>. Elde edilen <xref:System.ServiceModel.Discovery.FindResponse> ardından uygun ve beklenen XML öğeleri için sorgulanır. Bu öğelerden sonra konsola yazdırılır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi oluşturun.  
  
2.  İlk [çözüm temel dizin] \service\bin\debug içinde oluşturulan hizmet uygulamayı çalıştırın ve ardından [çözüm temel dizin] \Client\bin\debug oluşturulan istemci uygulaması çalıştırın  
  
3.  Hizmetin çevrimiçi olduğunu, istemci hizmeti bulur ve meta veri uç yayımlanan yazdırır dikkat edin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Ayrıca Bkz.
