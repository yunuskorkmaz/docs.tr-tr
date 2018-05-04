---
title: Görsel iş akışı izleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a185bb7a1e0d9d0d3466dc8e48cb0d0100702abe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="visual-workflow-tracking"></a>Görsel iş akışı izleme
Bu örnek aracılığıyla kullanılabilen hata ayıklama işlevini kullanarak uygulama izleme görsel bir iş akışını yazmak gösterilmiştir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Uygulama (Workflow.xaml içinde tanımlanmıştır) basit akış iş akışı yürütür ve şu anda yürütülen iş akışı görüntülemek için iş akışı Tasarımcısı yeniden barındırır. İş akışı yürütülen gibi şu anda yürütülen etkinlik sarı bir anahat ve hata ayıklama ok ile gösterilir. Ayrıca, iş akışı tarafından oluşturulan izleme kayıtları da uygulama penceresinde görüntülenir. İş akışı izleme hakkında daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). İş Akışı Tasarımcısı'nı yeniden barındırma hakkında daha fazla bilgi için bkz: [iş akışı Tasarımcısı yeniden barındırılmasını](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 İş akışı simulator iki sözlük tutarak çalışır. Şu anda yürütülen etkinliği nesnesi ve etkinlik örneği XAML satır numarası arasında bir eşleme içeriyor. Diğer Etkinlik örnek kimliği ve etkinlik nesne arasında bir eşleme içerir. Özel bir kullanarak izleme kayıtları yayılan profil, izleme uygulama şu anda yürütülen etkinlik örnek kimliği belirler ve geri Bu örneği XAML dosyaya eşler. Rehosted iş akışı Tasarımcısı'nı, Tasarımcı yüzeyine faaliyete vurgulayın ve özellikle etkinlik sarı kenarlık çizim ve sol tarafında sarı bir ok görüntüleme iş akışı hata ayıklayıcı gibi aynı yöntemi kullanmak için talimatı verilir Tasarımcısı.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Örnek dizininden WorkflowSimulator.sln dosyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Örneği çalıştırmak için CTRL + F5 tuşuna basın. Bu Workflow.xaml dosya rehosted iş akışı Tasarımcısı penceresinde görüntüler.  
  
4.  Tıklatın **dosya** menü ve seçin **iş akışını Çalıştır...** .  
  
5.  Bildirim şu anda yürütülen etkinlik daha önce açıklandığı şekilde vurgulanır ve izleme kayıtları uygulama penceresinin sağ tarafında görüntülenir.  
  
6.  İş akışı tamamlandığında karşılık gelir hangi etkinlik incelenecek izleme kayıtları tıklatabilirsiniz.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`