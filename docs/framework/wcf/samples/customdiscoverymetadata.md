---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465583"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Bu örnek, bulma meta veriler hizmet tarafından sunulan bulunabilirlik bir uç nokta için özel XML meta veri eklemeye gösterilmektedir. Örnek sonra nasıl bir istemci hizmeti için arama yapın ve bu özel verileri ayıklamak gösterir. Bu örnek, iki proje, hizmet ve istemci oluşur.  
  
## <a name="service"></a>Hizmet  
 İçinde `main` yöntemi, örnek gösterir, bir nesne türü <xref:System.Xml.Linq.XElement> istenen alanları ile doldurulur ve eklendiğinden <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için belirli bir uç noktası eklenir. Belirli uç noktanın bulunduğunda bulma buraya eklenen özel verileri içerir.  
  
## <a name="client"></a>İstemci  
 Örnek gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> üzerinde çağrılan yöntemi bir <xref:System.ServiceModel.Discovery.DiscoveryClient>. Ortaya çıkan <xref:System.ServiceModel.Discovery.FindResponse> ardından uygun ve beklenen XML öğeleri için sorgulanır. Bu öğeleri daha sonra konsola yazdırılır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi derleyin.  
  
2.  İlk [çözüm temel dizini] \service\bin\debug içinde oluşturulan hizmet uygulamayı çalıştırın ve ardından [çözüm temel dizini] \Client\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın  
  
3.  Hizmetin çevrimiçi duruma, istemci hizmeti bulur ve meta veri uç noktasında yayımlanan yazdırır dikkat edin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Ayrıca Bkz.
