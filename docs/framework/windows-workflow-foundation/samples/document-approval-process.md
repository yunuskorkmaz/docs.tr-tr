---
title: Belge Onay İşlemi
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: cee43aff991f9482de7b3172174eb0e786ec1fe6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710844"
---
# <a name="document-approval-process"></a>Belge Onay İşlemi

Bu örnek, birçok Windows Workflow Foundation (WF) ve Windows Communication Foundation (WCF) özelliklerinin birlikte kullanımını gösterir. Birlikte bir belge onay süreci senaryosu uygular. İstemci uygulaması, belgeleri onay ve onaylama için gönderebilir. İstemciler arasındaki iletişimleri kolaylaştırmak ve onay işleminin kurallarını zorlamak için bir onay Yöneticisi uygulaması vardır. Onay süreci, çeşitli onay türlerini yürütebilmesi için bir iş akışıdır. Tek bir onay, bir çekirdek onayı (bir onaylayanlar kümesinin yüzdesi) ve bir dizideki bir çekirdekte ve tek bir onaydan oluşan karmaşık bir onay işlemi almak için etkinlik vardır.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a>Örnek Ayrıntılar

Aşağıdaki grafik belge onay süreci iş akışını göstermektedir:

![Bir belge onay işlemi iş akışı](./media/document-approval-process/document-approval-process.jpg)

İstemci perspektifinden, onay işlemi aşağıdaki gibi çalışır:

1. İstemci, onay işlem sisteminde bir kullanıcı olarak abone olur.

2. WCF istemcisi, onay Yöneticisi uygulaması tarafından barındırılan bir WCF hizmetine gönderilir.

3. İstemciye benzersiz bir kullanıcı KIMLIĞI döndürülür. İstemci artık onay işlemlerine katılabilir.

4. Bir istemci birleştirildikten sonra tek, çekirdek veya karmaşık onay süreçlerini kullanarak bir belgeyi onaya gönderebilir.

5. İstemci arabirimindeki bir düğmeye tıkladıktan sonra istemci Iş akışı hizmet ana bilgisayarında bir iş akışı örneği başlatılıyor.

6. İş akışı, onay Yöneticisi uygulamasına bir onay isteği gönderir.

7. Workflow Manager, bir onay işlemini göstermek için kendi tarafında bir iş akışı başlatır.

8. Yönetici onayı iş akışı yürütüldükten sonra sonuçlar istemciye geri gönderilir.

9. İstemci sonuçları görüntüler.

10. İstemci bir onay isteği alabilir ve herhangi bir zamanda istek için yanıt verebilir.

11. İstemcide barındırılan bir WCF hizmeti, onay Yöneticisi uygulamasından bir onay isteği alabilir.

12. Belge bilgileri, gözden geçirilmek üzere istemcisinde sunulur.

13. Kullanıcı belgeyi onaylayabilir veya reddedebilir.

14. Bir WCF istemcisi, bir onay yanıtını onay Yöneticisi uygulamasına geri göndermek için kullanılır.

Onay Yöneticisi uygulamasının görünüm noktasından, onay işlemi aşağıdaki gibi çalışır:

1. İstemci onay işlem sistemine katılmayı ister.

2. Onay yöneticisinde bir WCF hizmeti, onay işlem sisteminin bir parçası olarak bir istek alır.

3. İstemci için benzersiz bir KIMLIK oluşturulur. Kullanıcı bilgileri bir veritabanında depolanır.

4. Benzersiz KIMLIK kullanıcıya geri gönderilir.

5. Bir onay isteği alma. Onay Yöneticisi bir onay işlemi yürütür.

6. Onay Yöneticisi tarafından yeni bir iş akışı başlatılıyor onay isteği alındı.

7. İsteğin türüne (basit, çekirdek veya karmaşık) bağlı olarak farklı bir etkinlik yürütülür.

8. İlişki ile gönderme ve alma etkinlikleri, gözden geçirme için istemciye onay isteği göndermek ve yanıtı almak için kullanılır.

9. Onay süreci iş akışının sonucu istemciye gönderilir.

## <a name="using-the-sample"></a>Örneği kullanma

##### <a name="to-set-up-the-database"></a>Veritabanını ayarlamak için

1. Yönetici ayrıcalıklarıyla açılan bir Visual Studio 2010 komut isteminden, bu belgeleyici klasörüne gidin ve Setup. cmd ' yi çalıştırın.

##### <a name="to-set-up-the-application"></a>Uygulamayı ayarlamak için

1. Visual Studio 2010 kullanarak, Belgetapprovalprocess. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için **Çözüm Gezgini** onay Yöneticisi uygulamasını başlatın ve sağ tıklama menüsünden **Hata Ayıkla**->yeni örnek **Başlat** ' a tıklayın.

    Yöneticinin çıkışının, olduğunu bilmenizi sağlamak için bekleyin.

##### <a name="to-run-the-single-approval-scenario"></a>Tek onay senaryosunu çalıştırmak için

1. Yönetici izniyle bir komut istemi açın.

2. Çözümü içeren dizine gidin.

3. ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin iki örneğini yürütün.

4. **Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.

5. Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın. Bir istemci için `UserType1` ve diğer tür `UserType2`kullanın.

6. `UserType1` istemcisinde, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın. **Onay iste**' ye tıklayın.

7. `UserType2` istemcisinde onay bekleyen bir belge görüntülenir. Seçin ve **Onayla** veya **Reddet**' e basın. Sonuçların `UserType1` istemcisinde gösterilmesi gerekir.

##### <a name="to-run-the-quorum-approval-scenario"></a>Çekirdek onay senaryosunu çalıştırmak için

1. Yönetici izniyle bir komut istemi açın.

2. Çözümü içeren dizine gidin.

3. ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin üç örneğini yürütün.

4. **Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.

5. Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın. Tek bir istemci için `UserType1` ve diğer iki tür `UserType2`.

6. `UserType1` istemcisinde, açılan menüden çekirdek onay türünü seçin ve bir belge adı ve içerik yazın. **Onay iste**' ye tıklayın. Bu, iki `UserType2` istemcisinin belgeyi onaylamasını veya reddetmesini ister. `UserType2` istemcilerinin her ikisi de yanıt vermesi gerekir, ancak belgeyi onaylanacak şekilde yalnızca bir istemci onaylaması gerekir.

7. `UserType2` istemcilerde, onay bekleyen bir belge görüntülenir. Seçin ve **Onayla** veya **Reddet**' e basın. Sonuçların `UserType1` istemcisinde gösterilmesi gerekir.

##### <a name="to-run-the-complex-approval-scenario"></a>Karmaşık onay senaryosunu çalıştırmak için

1. Yönetici izniyle bir komut istemi açın.

2. Çözümü içeren dizine gidin.

3. ApprovalClient\Bin\Debug klasörüne gidin ve ApprovalClient. exe ' nin dört örneğini yürütün.

4. **Keşfet**' e tıklayın, **abone ol** düğmesi etkin olana kadar bekleyin.

5. Herhangi bir Kullanıcı adı yazın ve **abone ol**' a tıklayın. Tek bir istemci için `UserType1`, iki kullanım türü `UserType2`ve son kullanımda `UserType3`.

6. `UserType1` istemcisinde, açılan menüden tek onay türünü seçin ve bir belge adı ve içerik yazın. **Onay iste**' ye tıklayın.

7. `UserType2` istemcilerde, onay bekleyen bir belge görüntülenir. Seçin ve **Onayla**' ya basın, belge `UserType3` istemcisine geçirilir.

    Belge ilk `UserType2` çekirdeği tarafından onaylanırsa, belge `UserType3` istemcisine geçirilir.

8. `UserType3` istemcisinden belgeyi onaylayın veya reddedin. Sonuçların `UserType1` istemcisinde gösterilmesi gerekir.

##### <a name="to-clean-up"></a>Temizlemek için

1. Visual Studio 2010 komut isteminden, Belgetapprovalprocess klasörüne gidin ve Cleanup. cmd ' yi çalıştırın.
