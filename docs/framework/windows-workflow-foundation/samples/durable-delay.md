---
title: Dayanıklı gecikme
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406582"
---
# <a name="durable-delay"></a>Dayanıklı gecikme
Bu örnek, iş akışı kalıcı bir cihaza gecikme sırasında devam eden bir gecikmenin bir dayanıklı gecikme kullanmayı gösterir. Örnek iş akışı tarafından bir gecikme ayrılmış iki ileti konsola içerir. Gecikme tetiklendiğinde, iş akışı kaldırıldı ve bellekte yeniden yükleniyor önce 5 saniye içinde iş akışı örnek deposu bekler.  
  
## <a name="workflow-details"></a>İş akışı ayrıntıları  
 İş akışı hizmeti konağı, iş akışını barındıran ve iş akışı örneği yükleme ve bunları kaldırma tarafından yönetir. Örnek iş akışı tanımının örneği başlatmak için bir ileti gönderen bir proxy ayarlar <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Özelliği `true`, bir ileti aldıktan sonra iş akışının yeni bir örneğini oluşturmak için etkinleştiriliyor.  
  
 Aşağıdaki liste iş akışı hizmeti ana bilgisayarı tarafından Kurulum başlatma sırasında ayrıntılı olarak açıklanmaktadır.  
  
1.  Bir adresi bir hizmet konağı oluşturur (http://localhost:8080/Client).  
  
2.  Hizmet ana bilgisayarı ile iletişimi etkinleştirmek için bir uç nokta oluşturur <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde.  
  
3.  Bir SQL örneği deposu ayarlar.  
  
4.  SQL kalıcı depolama için bir iş akışı örneği iş akışı hizmeti konağı kaldırma koşulları belirten bir kaldırma örneği davranışı ekler. Bu örnek için (gecikme tetiklendiğinde) iş akışı boş göründükten hemen sonra örneğini kaldırır.  
  
5.  İleti gönderen bir proxy oluşturur <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kalıcılık veritabanı ayarlama.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Gidin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  WorkflowManagementService.exe.config dosyasını düzenleyin ve içine aşağıdaki bağlantı dizesi Ekle <`database`> öğesi.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  DurableDelay\CS dizine gidin.  
  
    5.  Setup.cmd'yi çalıştırın.  
  
2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklayarak yükseltilmiş izinler kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.  
  
3.  Delay.sln çözüm dosyasını açın.  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
#### <a name="to-uninstall-this-sample"></a>Bu örnek kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelay\CS dizine gidin.  
  
3.  CleanUp.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`