---
title: "Arabelleğe alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7a486d3fbfb520ffe3b32c392566e5147c5dfcc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="buffered-receive"></a>Arabelleğe alma
Bu örnek ayarlama ve yapılandırma için arabellekli alma özelliği gösterilmektedir [!INCLUDE[wf](../../../../includes/wf-md.md)]. Arabelleğe alma iletilerin alındığını sırası hakkında endişelenmenize gerek olmadan bir iş akışı oluşturmak iş akışı Yazar verir. Arabellekli alma özelliği, yerel olarak iletileri arabelleğe alır ve iş akışı almaya hazır olduğunda bunları sunar.  
  
## <a name="demonstrates"></a>Gösteriler  
 Düzen dışı ileti işleme arabelleğe almak kullanarak Mesajlaşma etkinlikleriyle.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte, bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti kullanılarak gerçekleştirilir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ve bir dizi <xref:System.ServiceModel.Activities.Receive> etkinlikler. Bu iş akışını iş akışı bir kredi onaylanması için üç bildirimleri burada bekliyor basit kredi onay işlemi modeller. A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci uygulaması ne hizmet bekliyor ters sırada üç bağlantılı bildirim gönderir. Arabellekli alma özelliği hizmeti açık olduğu için her düzen dışı ileti hizmeti arabelleğe ve iş akışı, almaya hazır olduğunda işlenebilir.  
  
 Arabellekli alma özellik gerektirir <xref:System.ServiceModel.Activities.ReceiveContent> bağlama, bu nedenle hizmet Destek'ten kullanan <xref:System.ServiceModel.NetMsmqBinding>. Varsayılanların kullanıldığı şekilde özel yapılandırma bağlama için gereklidir.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Hizmet ayrıca hizmeti kullandığınız için meta verileri gösterir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Benzer şekilde, istemci uç noktası kullanılarak yapılandırılmış <xref:System.ServiceModel.NetMsmqBinding>. İstemci kodu ve yapılandırma oluşturulur kullanarak **hizmet Başvurusu Ekle** özelliği [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Aşağıdaki örnek, App.config dosyasında oluşturulan istemci uç noktadır.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]Yönetim uyumluluğu, metatabanı ve yapılandırma uyumluluğu  
  
3.  World Wide Web Hizmetleri, uygulama geliştirme özellikleri ve ASP.NET  
  
4.  Microsoft Message sıraları (MSMQ) sunucusu  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Konumunda bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, ASP.NET yazarak kaydolun `aspnet_regiis –I` ve ENTER tuşuna basın.  
  
2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.  
  
3.  LoanService.sln açın.  
  
4.  LoanService proje için sanal dizini oluşturmak isterseniz, seçin sorulduğunda **Evet**.  
  
#### <a name="to-set-up-the-service-queues"></a>Hizmet sıralarını ayarlamak için  
  
1.  Kuyruklar oluşturur ve Service1.xamlx içinde tanımlanan hizmet etkinleştirir LoanClient uygulamayı çalıştırmak için F5 tuşuna basın.  
  
2.  Açık **Bilgisayar Yönetimi** Compmgmt.msc bir komut isteminden çalıştırarak konsol.  
  
3.  İçinde **Bilgisayar Yönetimi** genişletin **hizmet**, **uygulamaları**, **Message Queuing**, **özel sıralar** .  
  
4.  Loanservice/service1.xamlx sıranın sağ tıklatıp **özellikleri**.  
  
5.  Seçin **güvenlik** sekmesini tıklatın ve eklemek **herkes alır ileti**, **iletiye** ve **iletisi gönder** izinleri.  
  
6.  Açık [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Yöneticisi.  
  
7.  Gözat **Server**, **siteleri**, **varsayılan Web sitesi**, **özel**, **LoanService** ve seçin **Gelişmiş Seçenekleri**  
  
8.  Değişiklik **etkin protokoller** olmasını **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Hizmetinin çalıştığından emin olmak için http://localhost/private/loanservice/service1.xamlx göz atın.  
  
2.  LoanClient uygulamayı çalıştırmak için F5 tuşuna basın. İş akışı tamamlandığında, bir out.txt dosyası ileti değişimi sonucunu içeren C:\Inbox kaydedilmesi gerekir.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1.  Açık **Bilgisayar Yönetimi** Compmgmt.msc bir komut isteminden çalıştırarak konsol.  
  
2.  Genişletme **hizmet** ve **uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
3.  Loanservice/service1.xamlx kuyruğu silin.  
  
4.  C:\Inbox dizini kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
