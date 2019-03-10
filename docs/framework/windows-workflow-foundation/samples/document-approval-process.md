---
title: Belge onay işlemi
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: d1e37dcbc21239822937c57d9779a52357aac518
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717719"
---
# <a name="document-approval-process"></a>Belge onay işlemi
Bu örnek, birlikte birçok Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF) özelliklerinin kullanımını gösterir. Birlikte bir belge onay işlemi senaryosu uygulayın. Bir istemci uygulaması, belgeler için onay gönderin ve onaylayın belgeleri. Kurallar onay işlemi uygular ve istemciler arasındaki iletişimi kolaylaştırmak için bir onay Yöneticisi uygulaması yok. Onay, onay çeşitli yürütebilen bir iş akışı işlemidir. Etkinlikler, tek bir onay, çekirdek onay (onaylayanlara kümesini yüzdesi) ve bir çekirdek ve dizideki tek onay içeren bir karmaşık bir onay işlemi mevcut.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki grafikte belge onay işlemi iş akışı gösterilmektedir.  
  
 ![Bir belge onay işlemi iş akışı](./media/approvalprocess.jpg "ApprovalProcess")  
  
 İstemcinin açısından bakıldığında, onay işlemi işlevleri gibi:  
  
1.  Bir istemci, bir kullanıcı onayı işlemi sistemde olacak şekilde abone olur.  
  
2.  Bir WCF istemcisi onay Yöneticisi uygulama tarafından barındırılan bir WCF hizmetine gönderir.  
  
3.  Benzersiz bir kullanıcı kimliği, istemciye döndürülür. İstemci, artık onay işlemde katılabilir.  
  
4.  Birleştirilmiş sonra bir istemci bir belge onay tek kullanarak, çekirdek veya karmaşık onaylama işlemlerini gönderebilirsiniz.  
  
5.  İstemcinin arabiriminde bir düğmeye tıkladı, bir iş akışı örneği iş akışı hizmeti ana bilgisayarı istemci olarak başlatılıyor.  
  
6.  İş akışı, onay manager uygulaması için bir onay isteği gönderir.  
  
7.  İş Akışı Yöneticisi, bir onay işlemi temsil etmek için kendi tarafında bir iş akışı başlatır.  
  
8.  Yönetici onayı iş akışı yürüten sonra sonuçları istemciye geri gönderilir.  
  
9. İstemci, sonuçları görüntüler.  
  
10. Bir istemci, bir onay isteği alır ve herhangi bir noktada isteğine zamanında yanıt.  
  
11. İstemci üzerinde barındırılan bir WCF hizmeti bir onay isteği onay Yöneticisi uygulamadan alabilir.  
  
12. Belge bilgilerini gözden geçirme için istemcide sunulur.  
  
13. Kullanıcı onaylayabileceğiniz veya reddedebileceğiniz belge.  
  
14. Bir WCF istemcisi, bir onay yanıtı onay Yöneticisi uygulamaya göndermek için kullanılır.  
  
 Onay Yöneticisi uygulama açısından bakıldığında, onay işlemi işlevleri gibi:  
  
1.  Bir istemci, onay işlemi sisteme katılmak ister.  
  
2.  Onay Yöneticisi bir WCF hizmeti bir isteği onaylama işlemi sisteminin bir parçası olarak alır.  
  
3.  İstemci için benzersiz bir kimlik oluşturulur. Kullanıcı bilgilerini bir veritabanında depolanır.  
  
4.  Benzersiz kimliği kullanıcıya geri gönderilir.  
  
5.  Bir onay isteği alma ' dir. Onay Yöneticisi bir onay işlemi yürütür.  
  
6.  Bir onay isteği yeni bir iş akışı başlatılıyorsa onay Yöneticisi tarafından alınır.  
  
7.  (Basit, çekirdek veya karmaşık) istek türüne bağlı olarak farklı bir etkinlik yürütülür.  
  
8.  Gönderme ve alma bağıntı etkinliklerle onay isteğini gözden geçirme için istemci gönderme ve yanıt almak için kullanılır.  
  
9. Onay işlemi iş akışı sonucu istemciye gönderilir.  
  
## <a name="using-the-sample"></a>Örnek kullanma  
  
##### <a name="to-set-up-the-database"></a>Veritabanı ayarlamak için  
  
1.  Yönetici ayrıcalıklarıyla açılan bir Visual Studio 2010 Komut isteminde bu DocumentApprovalProcess klasörüne gidin ve Setup.cmd'yi çalıştırın.  
  
##### <a name="to-set-up-the-application"></a>Uygulamayı kurmak için  
  
1.  Visual Studio 2010 kullanarak DocumentApprovalProcess.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için ApprovalManager projeye sağ tıklayarak onay Yöneticisi uygulamasını başlatma **Çözüm Gezgini** tıklayıp **hata ayıklama**->**Başlat**  sağ tıklatma menüsünden Yeni bir örneği.  
  
     Hazır olduğunu bildiren manager'ın çıktı için bekleyin.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Tek onayı senaryosu çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözümü içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve iki örneğini ApprovalClient.exe yürütün.  
  
4.  Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.  
  
5.  Herhangi bir kullanıcı adı yazın ve tıklayın **abone**. Bir istemci için kullanmak `UserType1` ve diğer tür `UserType2`.  
  
6.  İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklayın **onay isteği**.  
  
7.  İçinde `UserType2` istemci, onay bekleyen bir belge görüntülenir. Görseli seçip **onaylama** veya **Reddet**. Sonuçlar göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Çekirdek onayı senaryosu çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözümü içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve ApprovalClient.exe üç örneği çalıştırın.  
  
4.  Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.  
  
5.  Herhangi bir kullanıcı adı yazın ve tıklayın **abone**. Bir istemci için kullanmak `UserType1` ve diğer iki tür `UserType2`.  
  
6.  İçinde `UserType1` çekirdek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklayın **onay isteği**. Bu isteyen iki `UserType2` istemcileri onaylayabileceğiniz veya belge. Her ikisi de while `UserType2` istemcilerin gerekir yanıt, yalnızca bir istemci onaylanması için belgeyi onaylamanız gerekir.  
  
7.  İçinde `UserType2` istemciler, onay bekleyen bir belge görüntülenir. Görseli seçip **onaylama** veya **Reddet**. Sonuçlar göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Karmaşık onayı senaryosu çalıştırmak için  
  
1.  Yönetici izni olan bir komut istemi açın.  
  
2.  Çözümü içeren dizine gidin.  
  
3.  ApprovalClient\Bin\Debug klasöre gidin ve dört örneklerini ApprovalClient.exe yürütün.  
  
4.  Tıklayın **Bul**, bekle **abone** düğmesi etkinleşir.  
  
5.  Herhangi bir kullanıcı adı yazın ve tıklayın **abone**. Bir istemci için kullanmak `UserType1`, iki tür kullanan `UserType2`ve son kullanımda `UserType3`.  
  
6.  İçinde `UserType1` tek onay açılan menüden yazıp bir belge adı ve içerik istemci, seçin. Tıklayın **onay isteği**.  
  
7.  İçinde `UserType2` istemciler, onay bekleyen bir belge görüntülenir. Görseli seçip **onaylama**, belge gönderilirse `UserType3` istemci.  
  
     İlk belge onaylanırsa `UserType2` çekirdek, belge geçirildiğinde `UserType3` istemci.  
  
8.  Onaylama veya reddetme belgeden `UserType3` istemci. Sonuçlar göstermesi gerekir `UserType1` istemci.  
  
##### <a name="to-clean-up"></a>Temizlemek için  
  
1.  Bir Visual Studio 2010 komut isteminden DocumentApprovalProcess klasöre gidin ve Cleanup.cmd çalıştırın.
