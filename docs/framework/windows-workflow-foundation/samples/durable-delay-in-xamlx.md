---
title: Xamlx'de dayanıklı gecikme
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708691"
---
# <a name="durable-delay-in-xamlx"></a>Xamlx'de dayanıklı gecikme
Bu örnek, iş akışı kalıcı bir cihaza gecikme sırasında devam eden bir gecikmenin bir dayanıklı gecikme kullanmayı gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Tartışma  
 Örnek iş akışı tarafından bir gecikme ayrılmış iki ileti yerel bir dosyaya içerir. Gecikme tetiklendiğinde, iş akışı kaldırıldı ve bellekte yeniden yükleniyor önce 5 saniye içinde iş akışı örnek deposu bekler.  
  
 Visual Studio'da barındırılan bir iş akışı hizmeti .xamlx dosyasıdır. Visual Studio iş akışı iş akışı hizmeti konağı için konak kullanan Cassini'ye kullanır.  
  
 İş akışı barındırma yanı sıra, iş akışı hizmeti konağı iş akışı örneği yükleniyor ve bunları kaldırma yönetir. Windows Workflow Foundation (WF) tanımını (iş akışı hizmeti konağı) örneği başlatmak için bir ileti gönderen bir istemci ayarlama <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik. Bu <xref:System.ServiceModel.Activities.Receive> sahip kendi <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> özelliğini `true`, bir ileti aldıktan sonra iş akışının yeni bir örneğini oluşturmak için etkinleştiriliyor.  
  
 Başlatma sırasında bir kaldırma örneği davranışı altında Kalıcılık mağazayı (veritabanı) örneğine kaldırın iş akışı hizmeti konağı için belirten yapılandırma dosyasına eklenir. Bu örnek için (gecikme tetiklendiğinde) iş akışı boş göründükten hemen sonra örneğini kaldırır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelayXamlx\CS klasöre gidin.  
  
3.  Setup.cmd'yi çalıştırın.  
  
4.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.  
  
5.  DurableDelayXamlx.sln çözüm dosyasını açın.  
  
6.  İçinde **Çözüm Gezgini**, çözümü sağ tıklatın ve seçin **özellikleri**.  
  
7.  Seçin **birden fazla başlangıç projesi** ve her iki proje kümesine **Başlat**.  
  
8.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
9. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
#### <a name="to-uninstall-this-sample"></a>Bu örnek kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelayXamlx\CS klasöre gidin.  
  
3.  CleanUp.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
