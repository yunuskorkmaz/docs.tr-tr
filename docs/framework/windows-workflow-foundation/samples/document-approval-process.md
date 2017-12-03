---
title: "Belge onay işlemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 345fb44bed207d5d5e2c30bf4dd6e6ace27d7511
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="document-approval-process"></a>Belge onay işlemi
Bu örnek birçok kullanımını gösteren [!INCLUDE[wf](../../../../includes/wf-md.md)] ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] özellikleri birlikte. Birlikte bir belge onay işlemi senaryosu uygulayın. Bir istemci uygulaması onay için belge gönderme ve belgeleri onaylayabilirsiniz. Onay Yöneticisi uygulamanın istemciler arasındaki iletişimi kolaylaştırmak için ve onay işlemi kurallarını zorunlu tutmak için bulunmaktadır. Onay, onay çeşitli türlerde yürütebilir bir iş akışı işlemidir. Etkinlikleri tek bir onay, çekirdek onay (onaylayanlar kümesi yüzdesi) ve çekirdek ve bir sırada tek onay oluşan bir karmaşık onay işlemi almak için mevcut.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki grafikte belge onay işlem akışı gösterilmektedir.  
  
 ![Bir belge onay işlemi iş akışını](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")  
  
 İstemcinin açısından bakıldığında, onay işlemini işlevleri gibi:  
  
1.  Bir istemci, bir kullanıcının onay işlemi sistemde olması için abone olur.  
  
2.  A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcinin gönderdiği için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] onay Yöneticisi uygulaması tarafından barındırılan hizmeti.  
  
3.  Benzersiz bir kullanıcı kimliği istemciye döndürülür. İstemci onayı işlemlerde şimdi katılabilirsiniz.  
  
4.  Birleştirilmiş sonra bir istemci onayı tek kullanarak, çekirdek veya karmaşık onay işlemleri için bir belge gönderebilir.  
  
5.  İstemcinin arabiriminde düğmesine tıklandığında, bir iş akışı örneği iş akışı hizmeti ana bilgisayarı istemci olarak başlatılıyor.  
  
6.  İş akışı onay manager uygulaması için bir onay isteği gönderir.  
  
7.  İş Akışı Yöneticisi iş akışı bir onay işlemini temsil edecek şekilde kendi tarafında başlatır.  
  
8.  Yöneticisi Onayı iş akışı yürütür sonra sonuçları istemcisine geri gönderilir.  
  
9. İstemci sonuçları görüntüler.  
  
10. Bir istemci, bir onay isteği alır ve herhangi bir noktada isteğine zamanında yanıt.  
  
11. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci üzerinde barındırılan hizmeti, bir onay isteği onayı manager uygulamasından alabilir.  
  
12. Belge bilgilerini gözden geçirme için istemcide sunulur.  
  
13. Kullanıcı onaylayabilir veya belgeyi reddeder.  
  
14. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bir onay yanıtı onay Yöneticisi uygulamaya geri göndermek için kullanılır.  
  
 Onay Yöneticisi uygulamanın açısından bakıldığında, onay işlemini işlevleri gibi:  
  
1.  Bir istemci onay işlemi sisteme katılmak ister.  
  
2.  A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] onay Yöneticisi hizmeti isteği onaylama işlemi sisteminin bir parçası olarak alır.  
  
3.  Benzersiz bir kimliği istemci için oluşturulur. Kullanıcı bilgilerini bir veritabanında depolanır.  
  
4.  Benzersiz kimliği kullanıcıya geri gönderilir.  
  
5.  Bir onay isteği alma ' dir. Onay Yöneticisi bir onay işlemini yürütür.  
  
6.  Yeni bir iş akışı başlatma onay Yöneticisi tarafından bir onay isteği alındı.  
  
7.  İstek (Basit, çekirdek veya karmaşık) türüne bağlı olarak farklı bir etkinliğe yürütülür.  
  
8.  Gönderme ve alma etkinlikleri bağıntı ile istemci gözden geçirme için onay isteği gönderin ve yanıt almak için kullanılır.  
  
9. Onay işlemi iş akışını sonucunu istemciye gönderilir.  
  
## <a name="using-the-sample"></a>Örnek kullanma  
  
##### <a name="to-set-up-the-database"></a>Veritabanını ayarlamak için  
  
1.  Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemini yönetici ayrıcalıklarıyla açıldı, bu DocumentApprovalProcess klasörüne gidin ve Setup.cmd çalıştırın.  
  
##### <a name="to-set-up-the-application"></a>Uygulamayı kurmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DocumentApprovalProcess.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için ApprovalManager projeye sağ tıklayarak onay Yöneticisi uygulama Başlat **Çözüm Gezgini** tıklatıp **hata ayıklama**->**Başlat**  sağ tıklatma menüsünden Yeni örneği.  
  
     Yöneticinin çıkış hazır olduğunu size bildirmek bekleyin.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Tek onay senaryo çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözüm içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe iki örneğini çalıştırın.  
  
4.  Tıklatın **Bul**, bekle **abone** düğmesi etkin.  
  
5.  Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**. Bir istemci için kullanmak `UserType1` ve diğer tür `UserType2`.  
  
6.  İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklatın **isteği onay**.  
  
7.  İçinde `UserType2` istemci, onay bekleyen bir belge görünür. Seçip basın **onaylama** veya **Reddet**. Sonuçları göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Çekirdek onay senaryo çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözüm içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe üç örneklerini yürütün.  
  
4.  Tıklatın **Bul**, bekle **abone** düğmesi etkin.  
  
5.  Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**. Bir istemci için kullanmak `UserType1` ve diğer iki tür `UserType2`.  
  
6.  İçinde `UserType1` çekirdek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklatın **isteği onay**. Bu isteyen iki `UserType2` istemcileri onaylayın ya da belge reddedin. Her ikisi de while `UserType2` istemcilerin gerekir yanıt, yalnızca bir istemci belge, onaylanması için onaylamanız gerekir.  
  
7.  İçinde `UserType2` istemciler, onay bekleyen bir belge görünür. Seçip basın **onaylama** veya **Reddet**. Sonuçları göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Karmaşık onay senaryo çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözüm içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe dört örneklerini yürütün.  
  
4.  Tıklatın **Bul**, bekle **abone** düğmesi etkin.  
  
5.  Herhangi bir kullanıcı adı yazın ve'ı tıklatın **abone**. Bir istemci için kullanmak `UserType1`, iki tür kullanıyor `UserType2`ve son kullanımda `UserType3`.  
  
6.  İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklatın **isteği onay**.  
  
7.  İçinde `UserType2` istemciler, onay bekleyen bir belge görünür. Seçip basın **onaylama**, belge geçirilir `UserType3` istemci.  
  
     Belge ilk tarafından onaylanırsa `UserType2` çekirdek, belge için geçirilir `UserType3` istemci.  
  
8.  Onaylama veya reddetme belgeden `UserType3` istemci. Sonuçları göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-clean-up"></a>Temizlemek için  
  
1.  Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, DocumentApprovalProcess klasörüne gidin ve Cleanup.cmd çalıştırın.