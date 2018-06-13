---
title: Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: e6129594df6170f94a06caa08a9f16e4770bbfd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501461"
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Ayrıca Bkz.
