---
title: Dayanıklı gecikmesi
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 5307b8144e17f91cd3ba8c2e385492f86c167820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516028"
---
# <a name="durable-delay"></a>Dayanıklı gecikmesi
Bu örnek, sağlam bir aygıt için iş akışı sırasında gecikme devam ederse gecikme dayanıklı bir gecikme kullanımı gösterilmiştir. Örnek iş akışı tarafından bir gecikme ayrılmış iki iletilerini konsola içerir. Gecikme tetiklendiğinde, iş akışı kaldırılır ve iş akışı örneği deposundaki 5 bellekte yeniden yükleniyor önce saniye bekler.  
  
## <a name="workflow-details"></a>İş akışı ayrıntıları  
 İş akışı hizmeti ana bilgisayarı, iş akışı barındırır ve yükleme ve bunları kaldırma iş akışı örneklerini yönetir. Örnek iş akışı tanımı örneği başlatmak için bir ileti gönderen bir proxy ayarlar <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Özelliği ayarlanmış `true`, iletiyi aldıktan sonra iş akışının yeni bir örneğini oluşturmak üzere etkinleştirme.  
  
 Aşağıdaki listede iş akışı hizmeti ana bilgisayarı tarafından Kurulum başlatma sırasında Ayrıntılar verilmiştir.  
  
1.  Hizmet ana bilgisayarı olan bir adresi oluşturur (http://localhost:8080/Client).  
  
2.  Hizmet ana bilgisayarı ile iletişimi etkinleştirmek için bir uç nokta oluşturuyor <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde.  
  
3.  Bir SQL örneği deposu ayarlar.  
  
4.  SQL Kalıcılık deposu için bir iş akışı örneği iş akışı hizmeti ana bilgisayarı kaldırma koşulları belirtir unload örneği davranışı ekler. Bu örnek için (gecikme tetiklendiğinde) iş akışı boşta göründükten hemen sonra örneğini kaldırır.  
  
5.  Bir ileti gönderir proxy oluşturur <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kalıcılık veritabanı ayarlama.  
  
    1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
    2.  Gidin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  WorkflowManagementService.exe.config dosyasını düzenleyin ve aşağıdaki bağlantı dizesi içinde eklemek <`database`> öğesi.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  DurableDelay\CS dizinine gidin.  
  
    5.  Setup.cmd çalıştırın.  
  
2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklayarak yükseltilmiş izinleri kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.  
  
3.  Delay.sln çözüm dosyasını açın.  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
#### <a name="to-uninstall-this-sample"></a>Bu örnek kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  DurableDelay\CS dizinine gidin.  
  
3.  CleanUp.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`