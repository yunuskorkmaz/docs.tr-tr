---
title: XAMLX dayanıklı gecikmesi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa5a9e4287bcbcb490754b84a8b5060d321f779
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="durable-delay-in-xamlx"></a>XAMLX dayanıklı gecikmesi
Bu örnek, sağlam bir aygıt için iş akışı sırasında gecikme devam ederse gecikme dayanıklı bir gecikme kullanımı gösterilmiştir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Tartışma  
 Örnek iş akışı tarafından bir gecikme ayrılmış iki iletileri yerel bir dosyaya içerir. Gecikme tetiklendiğinde, iş akışı kaldırılır ve iş akışı örneği deposundaki 5 bellekte yeniden yükleniyor önce saniye bekler.  
  
 Visual Studio'da barındırılan bir iş akışı hizmeti .xamlx dosyasıdır. Visual Studio, iş akışını bir iş akışı hizmeti ana kullanan Cassini kullanır.  
  
 İş akışı barındırma ek olarak, iş akışı hizmeti ana bilgisayarı iş akışı örnekleri yükleme ve bunları yüklemeyi kaldırma yönetir. Windows Workflow Foundation (WF) tanımı (iş akışı hizmeti ana bilgisayarı) örneği başlatmak için bir ileti gönderen istemci ayarlamak <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı. Bu <xref:System.ServiceModel.Activities.Receive> sahip kendi <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> özelliğini `true`, iletiyi aldıktan sonra iş akışının yeni bir örneğini oluşturmak üzere etkinleştirme.  
  
 Başlatma sırasında bir kaldırma örneği davranış altında kalıcı deponun (veritabanı) örneğini kaldırın iş akışı hizmeti ana bilgisayarı belirtir yapılandırma dosyasının eklenir. Bu örnek için (gecikme tetiklendiğinde) iş akışı boşta göründükten hemen sonra örneğini kaldırır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelayXamlx\CS klasöre gidin.  
  
3.  Setup.cmd çalıştırın.  
  
4.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.  
  
5.  DurableDelayXamlx.sln çözüm dosyasını açın.  
  
6.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve seçin **özellikleri**.  
  
7.  Seçin **birden fazla başlangıç projesi** ve her iki proje kümesine **Başlat**.  
  
8.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
9. Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
#### <a name="to-uninstall-this-sample"></a>Bu örnek kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelayXamlx\CS klasöre gidin.  
  
3.  CleanUp.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
