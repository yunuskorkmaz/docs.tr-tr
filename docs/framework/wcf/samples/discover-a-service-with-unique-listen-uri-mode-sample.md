---
title: "Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48b49def3f8f009eeb4ffa0204e9c616b5acfec7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği
Bu örnek, bir hizmet bulmak gösterilmiştir <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliğini <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Zaman <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique>, ListenUri güvence altına benzersiz olması için bağlantı noktası ayarlayarak veya yolun bir GUID ekleyerek benzersiz olması için benzersiz olmalıdır.  
  
### <a name="features-on-the-service"></a>Hizmet Özellikleri  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique> TCP uç noktası için. Hizmet ardından bulunabilirlik üzerinden yapılan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası.  
  
### <a name="features-on-the-client"></a>İstemci özellikleri  
 Bu istemci doğru kullanarak hizmete bağlanıyor `Via.Uri` kullanarak <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi. <xref:System.ServiceModel.Discovery.FindResponse> Sağlayıcıdan döndürülen yöntemi, sonra da geçerli bir içerip içermediğini için sorgulanır <xref:System.ServiceModel.Endpoint.ListenUri%2A> ve farklı olup `Address.Uri`. Uygun bilgileri sonra geçirilir `InvokeCalculatorService` yöntemi. İçinde `InvokeCalculatorService` yöntemi, <xref:System.ServiceModel.Endpoint.ListenUri%2A> çağıran tarafından geçirilen sonra bir `ClientViaBehavior` doğru ile `Via.Uri` istemcinin uç noktasına eklenir.  
  
##### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], UniqueListenUriMode.sln açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  [Çözüm temel dizin] \service\bin\debug klasöründe oluşturulan hizmet uygulamayı çalıştırın.  
  
4.  [Çözüm temel dizin] \Client\bin\debug klasöründe oluşturulan istemci uygulaması çalıştırın.  
  
     İstemci çalışan hizmetin bulur ve hizmetin uç noktası tarafından yayımlanan meta verileri konsola yazar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Ayrıca Bkz.
