---
title: Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: 7e1c5ae0cb1a44c72a27566035b4bc20acbf1614
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748135"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği
Bu örnek, bir hizmet bulma gösterir <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliğini <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Zaman <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliği <xref:System.ServiceModel.Description.ListenUriMode.Unique>, ListenUri bağlantı noktası benzersiz olacak şekilde ayarlayarak ya da yolun bir GUID eklenerek benzersiz olması için benzersiz olmasını güvence altına.  
  
### <a name="features-on-the-service"></a>Hizmet Özellikleri  
 <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Özelliği <xref:System.ServiceModel.Description.ListenUriMode.Unique> TCP uç noktası için. Hizmet ardından bulunabilirlik üzerinden yapılan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası.  
  
### <a name="features-on-the-client"></a>İstemci özellikleri  
 Bu istemci, doğru kullanarak hizmete bağlanır `Via.Uri` kullanarak <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi. <xref:System.ServiceModel.Discovery.FindResponse> Sağlayıcıdan döndürülen yöntemi, daha sonra geçerli bir içerip içermediğini için sorgulanır <xref:System.ServiceModel.Endpoint.ListenUri%2A> ve farklı olup `Address.Uri`. Uygun bilgileri geçirilerek `InvokeCalculatorService` yöntemi. İçinde `InvokeCalculatorService` yöntemi <xref:System.ServiceModel.Endpoint.ListenUri%2A> çağıran tarafından geçirilen bir `ClientViaBehavior` doğru ile `Via.Uri` istemcinin uç noktasına eklediniz.  
  
##### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], UniqueListenUriMode.sln açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  [Çözüm temel dizini] \service\bin\debug klasöründe oluşturulan hizmet uygulaması çalıştırın.  
  
4.  [Çözüm temel dizini] \Client\bin\debug klasöründe oluşturulan istemci uygulamasını çalıştırın.  
  
     İstemci, çalışan hizmetin bulur ve hizmet uç noktası tarafından yayınlanan meta verileri konsola yazar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Ayrıca Bkz.
