---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b4a68204d8ae5d2a338d60498522810a557e575
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Ayrıca Bkz.
