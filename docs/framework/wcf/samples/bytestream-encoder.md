---
title: ByteStream Kodlayıcı
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: cbd4110ecc04923b79d6b910fcf7ab4ca2012680
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480698"
---
# <a name="bytestream-encoder"></a>ByteStream Kodlayıcı
Bu örnek nasıl oluşturulacağını gösterir. bir `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> , bayt akışı Kodlayıcı işlevselliğini gösterir.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, standart bir oluşturma işlemini gösterir <xref:System.ServiceModel.Channels.Binding> standart bağlama öğeleri kullanılarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Bu örnek, bayt akışı Kodlayıcı karşıya yükleme ve bir resim indirmek için nasıl kullanılacağını gösterir. Bayt akışı Kodlayıcısı özelliği yalnızca HTTP aktarımı destekler ve güvenilir Mesajlaşma veya güvenlik gibi özellikleri desteklemez. Yalnızca <xref:System.ServiceModel.Channels.MessageVersion> desteklenir <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Bu örnek çalıştırıyorsanız, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] veya [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], çalıştığından emin olun [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükseltilmiş ayrıcalıklara sahip.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  ByteStreamHttpBinding.sln açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözüm Gezgini'nde projeye sağ tıklatıp seçerek ByteStreamHttpBindingServer projeye yeni bir örneğini Başlat **hata ayıklama**, ardından **yeni örnek Başlat** bağlam menüsünden.  
  
3.  Çözüm Gezgini'nde projeye sağ tıklatıp seçerek ByteStreamHttpBindingClient projeye yeni bir örneğini Başlat **hata ayıklama**, **yeni örnek Başlat** bağlam menüsünden.
