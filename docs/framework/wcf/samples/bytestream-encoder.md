---
title: "ByteStream Kodlayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de6d5fd64046a72eb6a21b43dd977463f5619850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="bytestream-encoder"></a>ByteStream Kodlayıcı
Bu örnek nasıl oluşturulduğunu gösteren bir `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> bayt akışı Kodlayıcı işlevselliğini gösterir.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, bir standart oluşturmaya gösterilmiştir <xref:System.ServiceModel.Channels.Binding> standart bağlama öğeleri kullanılarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Bu örnek bayt akışı Kodlayıcı karşıya yükleyin ve bir görüntüsünü karşıdan yüklemek için nasıl kullanılacağını gösterir. Bayt akışı Kodlayıcı özelliği, yalnızca HTTP aktarımı destekler ve güvenilir Mesajlaşma veya güvenlik gibi özellikleri desteklemiyor. Yalnızca <xref:System.ServiceModel.Channels.MessageVersion> desteklenen olduğu <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Bu örnek çalıştırıyorsanız, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] veya [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], çalıştığından emin olun [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükseltilmiş ayrıcalıklarla.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  ByteStreamHttpBinding.sln dosyasında açma [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözüm Gezgini'nde projeye sağ tıklayıp seçerek ByteStreamHttpBindingServer proje yeni bir örneğini Başlat **hata ayıklama**ve ardından **başlangıç yeni örnek** ve bağlam menüsünden.  
  
3.  Çözüm Gezgini'nde projeye sağ tıklayıp seçerek ByteStreamHttpBindingClient proje yeni bir örneğini Başlat **hata ayıklama**, **başlangıç yeni örnek** ve bağlam menüsünden.
