---
title: Arabelleğe alma
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: b95577c71493275f30703b4366fab32a51097bd2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526810"
---
# <a name="buffered-receive"></a>Arabelleğe alma
Bu örnek, ayarlama ve arabelleğe alınmış alma özelliği, Windows Workflow Foundation (WF) yapılandırma gösterilmektedir. Arabelleğe alma iletilerin alındığı sıraya hakkında endişelenmenize gerek kalmadan bir iş akışı oluşturmak iş akışı Yazar sağlar. Arabelleğe alınmış alma özelliği, yerel olarak iletileri arabelleğe alır ve iş akışı almaya hazır olduğunda bunları sunar.  
  
## <a name="demonstrates"></a>Gösteriler  
 Düzen dışı ileti işleme arabelleğe kullanarak Mesajlaşma etkinlikleriyle alırsınız.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte, bir Windows Communication Foundation (WCF) hizmeti kullanılarak uygulanan [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ve bir dizi <xref:System.ServiceModel.Activities.Receive> etkinlikler. Bu iş akışı, bir basit kredi onay işlemi burada üç bildirimleri onaylanması bir kredi için iş akışı bekliyor modeller. Bir Windows Communication Foundation (WCF) istemci uygulama, hangi hizmet bekliyor, ters sırada bağıntılı olan üç bildirimleri gönderir. Hizmeti arabelleğe alınmış alma özelliği açık olduğundan her düzen dışı ileti hizmeti arabelleğe ve iş akışı, almaya hazır olduğunda işlenir.  
  
 Arabelleğe alınmış alma özelliği gerektirir <xref:System.ServiceModel.Activities.ReceiveContent> kullanır, bu nedenle hizmet bağlama Destek'ten <xref:System.ServiceModel.NetMsmqBinding>. Özel bir yapılandırma bağlama için gerekli olduğundan varsayılan değerler kullanılır.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Hizmetini kullanarak hizmet için meta verileri de gösteren <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Benzer şekilde, istemci uç noktası kullanılarak yapılandırılan <xref:System.ServiceModel.NetMsmqBinding>. İstemci kodu ve yapılandırması kullanarak oluşturulur **hizmet Başvurusu Ekle** Visual Studio özelliği. Aşağıdaki örnek, App.config dosyasında oluşturulan istemci uç noktadır.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Yönetim uyumluluğu, metatabanı ve yapılandırma uyumluluğu  
  
3.  World Wide Web Hizmetleri, uygulama geliştirme özellikleri ve ASP.NET  
  
4.  Microsoft ileti kuyrukları (MSMQ) sunucusu  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için  
  
1.  Konumunda bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut isteminde, ASP.NET yazarak kaydetme `aspnet_regiis –I` ve ENTER tuşuna basın.  
  
2.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.  
  
3.  LoanService.sln açın.  
  
4.  LoanService proje için sanal dizini oluşturmak istiyorsanız seçin. sorulduğunda **Evet**.  
  
#### <a name="to-set-up-the-service-queues"></a>Hizmet sıralarını ayarlamak için  
  
1.  Kuyruk oluşturan ve Service1.xamlx içinde tanımlanan hizmet etkinleştirir LoanClient uygulamayı çalıştırmak için F5 tuşuna basın.  
  
2.  Açık **Bilgisayar Yönetimi** bir komut istemi'nden Compmgmt.msc çalıştırarak Konsolu.  
  
3.  İçinde **Bilgisayar Yönetimi** genişletin **hizmet**, **uygulamaları**, **Message Queuing**, **özel sıralar** .  
  
4.  Loanservice/service1.xamlx sıranın sağ tıklayıp **özellikleri**.  
  
5.  Seçin **güvenlik** sekme ve Ekle **herkesin aldığında iletiyi**, **iletiye** ve **iletisi gönder** izinleri.  
  
6.  Açık [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Yöneticisi.  
  
7.  Gözat **sunucu**, **siteleri**, **varsayılan Web sitesi**, **özel**, **LoanService** seçin **Gelişmiş Seçenekleri**  
  
8.  Değişiklik **etkin protokoller** olmasını **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Gözat http://localhost/private/loanservice/service1.xamlx hizmetinin çalıştığından emin olmak için.  
  
2.  LoanClient uygulamayı çalıştırmak için F5 tuşuna basın. İş akışı tamamlandıktan sonra ileti alışverişi sonucunu içeren C:\Inbox out.txt dosya kaydedilmesi gerekir.  
  
#### <a name="to-clean-up"></a>Temizlemek için  
  
1.  Açık **Bilgisayar Yönetimi** bir komut istemi'nden Compmgmt.msc çalıştırarak Konsolu.  
  
2.  Genişletin **hizmet** ve **uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
3.  Loanservice/service1.xamlx sırayı silin.  
  
4.  C:\Inbox dizini kaldırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
