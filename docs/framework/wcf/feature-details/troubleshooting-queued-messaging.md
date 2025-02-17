---
description: Daha fazla bilgi için bkz. sıraya alınan Mesajlaşma sorunlarını giderme
title: Kuyruğa Alınan İletilerde Sorun Giderme
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: e7cf2706e7c0853f14bad449b6ecaa8dd5983755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733092"
---
# <a name="troubleshooting-queued-messaging"></a>Kuyruğa Alınan İletilerde Sorun Giderme

Bu bölüm, Windows Communication Foundation (WCF) içinde kuyrukları kullanmaya yönelik genel soruları ve sorun giderme yardımını içerir.

## <a name="common-questions"></a>Sık sorulan sorular

**S:** WCF Beta 1 ' i kullandım ve MSMQ düzeltmesini yükledim. Düzeltmeyi kaldırdım mıyım?

**Y:** Evet. Bu düzeltme artık desteklenmiyor. WCF artık bir düzeltme gereksinimi olmadan MSMQ üzerinde çalışmaktadır.

**S:** MSMQ için iki bağlama vardır: <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> . Ne zaman kullanmalıyım?

Y **:** <xref:System.ServiceModel.NetMsmqBinding>Ikı WCF uygulaması arasındaki sıraya alınmış iletişim IÇIN MSMQ 'yu bir taşıma olarak kullanmak istediğinizde kullanın. <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>Yenı WCF uygulamalarıyla iletişim kurmak için mevcut MSMQ uygulamalarını kullanmak istediğinizde kullanın.

**S:** Ve bağlamalarını kullanmak için MSMQ 'YU yükseltmem gerekiyor <xref:System.ServiceModel.NetMsmqBinding> `MsmqIntegration` mu?

Y **:** Eşleşen. Her iki bağlama da Windows XP ve Windows Server 2003 üzerinde MSMQ 3,0 ile çalışır. Windows Vista 'da MSMQ 4,0 sürümüne yükselttiğinizde bağlamaların bazı özellikleri kullanılabilir hale gelir.

**S:** MSMQ <xref:System.ServiceModel.NetMsmqBinding> 4,0 ' de ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bağlamaların hangi özellikleri mevcuttur, ancak MSMQ 3,0 ' de kullanılabilir mi?

Y **:** MSMQ 4,0 ' de şu özellikler mevcuttur, ancak MSMQ 3,0 ' de kullanılabilir:

- Özel atılacak mektup kuyruğu yalnızca MSMQ 4,0 ' de desteklenir.

- MSMQ 3,0 ve 4,0, zarar iletilerini farklı işler.

- Yalnızca MSMQ 4,0, uzaktan işlenen okumayı destekler.

Daha fazla bilgi için bkz. [Windows Vista, Windows Server 2003 ve WINDOWS XP 'de kuyruğa alma özellikleri](diff-in-queue-in-vista-server-2003-windows-xp.md).

**S:** MSMQ 3,0 ' I kuyruğa alınmış iletişimin bir tarafında ve diğer tarafta MSMQ 4,0 kullanabilir miyim?

**Y:** Evet.

**S:** Mevcut MSMQ uygulamalarını yeni WCF istemcileri veya sunucularıyla bütünleştirmek istiyorum. MSMQ altyapımın her iki tarafını da yükseltmem gerekiyor mu?

Y **:** Eşleşen. Her iki taraftan da MSMQ 4,0 sürümüne yükseltmeniz gerekmez.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölüm, en yaygın sorun giderme sorunlarının yanıtlarını içerir. Bilinen sınırlamalar olan bazı sorunlar da sürüm notlarında açıklanmıştır.

**S:** Özel bir sıra kullanmaya çalışıyorum ve şu özel durumu alıyorum: `System.InvalidOperationException` : URL geçersiz. Kuyruğun URL 'SI ' $ ' karakterini içeremez. Özel bir kuyruğu gidermek için net. MSMQ: gt Machine/Private/SıraAdı içindeki sözdizimini kullanın.

Y **:** Yapılandırmanızda ve kodunuzda sıra Tekdüzen Kaynak tanımlayıcısı 'nı (URI) denetleyin. URI 'de "$" karakterini kullanmayın. Örneğin, OrdersQueue adlı özel bir kuyruğu ele almak için URI 'yi olarak belirtin `net.msmq://localhost/private/ordersQueue` .

**S:** `ServiceHost.Open()` Sıraya alınan uygulamamda çağırmak şu özel durumu oluşturur: `System.ArgumentException` : temel adres bir URI sorgu dizesi içeremez. Neden?

Y **:** Yapılandırma dosyanızdaki ve kodunuzda sıra URI 'sini kontrol edin. MSMQ kuyrukları '? ' karakterinin kullanımını desteklese de URI 'Ler, bu karakteri bir dize sorgusunun başlangıcı olarak yorumlar. Bu sorunu önlemek için, '? ' karakterlerini içermeyen sıra adlarını kullanın.

**S:** Gönderme başarılı ancak alıcıda hiçbir hizmet işlemi çağrılmayacak. Neden?

Y **:** Yanıtı öğrenmek için aşağıdaki onay listesinden çalışın:

- İşlem sırası gereksinimlerinin belirtilen sigortalarla uyumlu olduğundan emin olun. Aşağıdaki ilkelere göz önünde edin:

  - Dayanıklı iletileri (veri birimleri ve oturumlar) <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  yalnızca bir işlem kuyruğuna "tam bir kez" Assura () ile gönderebilirsiniz `true` .

  - Yalnızca "tam bir kez" asi ile oturum gönderebilirsiniz.

  - İşlem sırasındaki bir oturumdaki iletileri almak için bir işlem gereklidir.

  - <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  `false` Yalnızca işlem olmayan bir sıraya () sahip olmayan geçici veya dayanıklı iletiler (yalnızca veri birimleri) gönderebilir veya alabilirsiniz.

- Atılacak ileti sırasını denetleyin. İletileri burada bulursanız, neden teslim edilmediğini saptayın.

- Bağlantı veya adresleme sorunları için giden kuyrukları denetleyin.

**S:** Özel bir atılacak ileti sırası belirttim, ancak gönderen uygulamayı başlattığımda, atılacak ileti sırasının bulunamadığını veya gönderen uygulamanın atılacak ileti kuyruğu için izin bulunmadığını belirten bir özel durum alıyorum. Bu neden gerçekleşiyor?

Y **:** Özel atılacak ileti sırası URI 'SI, ilk kesimde bir "localhost" veya bilgisayar adı (örneğin, net. MSMQ://localhost/private/myAppdead-letter Queue) içermelidir.

**S:** Her zaman özel bir atılacak ileti sırası tanımlanması veya varsayılan bir teslim edilemeyen ileti sırası olması gerekir mi?

Y **:** Asuriyler "tam olarak" ( <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  `true` ) ise ve özel bir atılacak ileti sırası belirtmezseniz, varsayılan sistem genelinde işlem atılacak ileti sırası olur.

Eğer asursları None ( <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  `false` ) ise, varsayılan, atılacak ileti sırası işlevselliği değildir.

**S:** Hizmetim SvcHost üzerinde oluşturulur. "EndpointListener Requirements ListenerFactory tarafından karşılanamıyor" iletisiyle birlikte aç. Neden?

A. Hizmet sözleşmenizi denetleyin. Tüm hizmet işlemlerine "ıoneway =" koymak için unutulmuş olabilirsiniz `true` . Kuyruklar yalnızca tek yönlü hizmet işlemlerini destekler.

**S:** Kuyrukta ileti var, ancak hiçbir hizmet işlemi çağrılmayacak. Sorun nedir?

Y **:** Hizmet ana bilgisayarın hatalı olup olmadığını belirleme. İzlemeye veya uygulamaya bakarak kontrol edebilirsiniz `IErrorHandler` . Bir zarar iletisi algılanırsa, varsayılan olarak hizmet ana bilgisayar hataları.

**S:** Kuyrukta iletiler var, ancak Web 'de barındırılan sıraya alınmış hizmetm etkinleştirilmiyor. Neden?

Y **:** En yaygın nedenler izinlerdir.

1. `NetMsmqActivator`İşlemin çalıştığından ve `NetMsmqActivator` işlemin kimliğine kuyrukta okuma ve arama izni verildiğinden emin olun.

2. , `NetMsmqActivator` Uzak bir makinedeki kuyrukları izliyorsanız, bunun `NetMsmqActivator` kısıtlı bir belirteç altında çalıştırılmadığından emin olun. Öğesini `NetMsmqActivator` Kısıtlanmamış bir belirteçle çalıştırmak için:

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

Güvenlikle ilgili olmayan Web ana bilgisayar sorunları için bkz. [kuyruğa alınmış bir uygulamayı barındıran Web](web-hosting-a-queued-application.md).

**S:** Oturumlara erişmenin en kolay yolu nedir?

Y **:** `true`Oturumdaki son iletiye karşılık gelen Işlemde AutoComplete = ve `false` kalan tüm hizmet Işlemlerinde Otomatik Tamamla = seçeneğini ayarlayın.

**S:** Hizmeti neden `ProtocolException` hem sıraya alınmış oturum iletilerini hem de sıraya alınmış veri birimi iletilerini içeren bir kuyruktan okurken neden bir oluştur?

Y **:** Sıraya alınan oturum iletilerinin ve sıraya alınmış veri birimi iletilerinin bulunduğu şekilde temel bir farklılık vardır. Bu nedenle, sıraya alınan bir oturum iletisini okumasını bekleyen bir hizmet, bir sıraya alınmış veri birimi iletisi alamıyor ve sıradaki bir veri birimi iletisini okumak için bekleyen bir hizmet oturum iletisi alamaz. Aynı sıradan her iki türdeki iletiyi okumaya çalışmak aşağıdaki özel durumu oluşturur:

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

Bir uygulama aynı bilgisayardan hem sıraya alınmış oturum iletileri hem de sıraya alınmış veri birimi iletileri gönderiyorsa, sistem atılacak ileti sırası ve özel bir atılacak mektup sırası özellikle bu soruna açıktır. Bir ileti başarıyla gönderilemezse, teslim edilemeyen ileti kuyruğuna taşınır. Bu koşullarda, teslim edilemeyen ileti kuyruğunda hem oturum hem de veri birimi iletileri olması mümkündür. Her iki türden iletiyi bir kuyruktan okurken çalışma zamanında ayırmanın bir yolu yoktur, bu nedenle uygulamalar aynı bilgisayardan hem sıraya alınmış oturum iletilerini hem de sıraya alınmış veri birimi iletilerini göndermemelidir.

### <a name="msmq-integration-specific-troubleshooting"></a>MSMQ tümleştirmesi: belirli sorun giderme

**S:** Bir ileti gönderdiğimde veya hizmet ana bilgisayarını açtığımda, düzenin yanlış olduğunu belirten bir hata alıyorum. Neden?

Y **:** MSMQ tümleştirme bağlamasını kullandığınızda, MSMQ. formatname şemasını kullanmanız gerekir. Örneğin, MSMQ. FormatName: DIRECT = OS: .\Private $ \OrdersQueue. Ancak özel atılacak ileti sırasını belirttiğinizde net. MSMQ şemasını kullanmanız gerekir.

**S:** Ortak veya özel biçim adı kullandığımda ve hizmet ana bilgisayarını Windows Vista 'da açtığınızda bir hata alıyorum. Neden?

Y **:** Windows Vista 'daki WCF tümleştirme kanalı, zarar iletilerini işlemek için ana uygulama kuyruğu için bir alt sıra açılıp açılmadığını denetler. Alt sıra adı, dinleyiciye geçirilen bir MSMQ. formatname URI 'sinden türetilir. MSMQ 'daki alt sıra adı yalnızca bir doğrudan biçim adı olabilir. Bu nedenle hatayı görürsünüz. Sıra URI 'sini doğrudan biçim adıyla değiştirin.

**S:** MSMQ uygulamasından bir ileti alırken ileti kuyrukta bulunur ve alan WCF uygulaması tarafından okunamaz. Neden?

Y **:** İletinin gövdeye sahip olup olmadığını denetleyin. İletinin gövdesi yoksa, MSMQ tümleştirme kanalı iletiyi yoksayar. `IErrorHandler`Özel durumlar hakkında bildirim almak ve izlemeleri denetlemek için uygulayın.

### <a name="security-related-troubleshooting"></a>Security-Related sorunlarını giderme

**S:** Çalışma grubu modunda varsayılan bağlama kullanan örneği çalıştırdığımda, iletiler gönderildi ancak alıcı tarafından hiçbir zaman alınmaz.

Y **:** Varsayılan olarak, iletiler Active Directory dizin hizmeti gerektiren MSMQ iç sertifikası kullanılarak imzalanır. Çalışma grubu modunda Active Directory kullanılamadığından, iletiyi imzalama başarısız olur. Bu nedenle ileti, "bozuk imza" gibi atılacak ileti sırası ve hata nedeninden sonra belirtilir.

Geçici çözüm, güvenliği devre dışı bırakır. Bu, <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> çalışma grubu modunda çalışmasını sağlamak için ayarıyla yapılır.

Başka bir geçici çözüm de <xref:System.ServiceModel.MsmqTransportSecurity> <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> özelliğinden yararlanmak ve olarak ayarlamak <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve istemci sertifikasını ayarlamak.

Ancak başka bir geçici çözüm de Active Directory tümleştirmeyle MSMQ yüklemektir.

**S:** Bir sıraya Active Directory için varsayılan bağlama (taşıma güvenliği açık) ile bir ileti gönderdiğimde, "iç sertifika bulunamadı" iletisini alıyorum. Bu Nasıl yaparım? düzeltilsin mi?

Y **:** Bu, gönderenin Active Directory sertifikanın yenilenmesi gerektiği anlamına gelir. Bunu yapmak için, **Denetim Masası**, **Yönetim Araçları**, **Bilgisayar Yönetimi**' ni açın, **MSMQ**' ya sağ tıklayın ve **Özellikler**' i seçin. **Kullanıcı sertifikası** sekmesini seçin ve **Yenile** düğmesine tıklayın.

**S:** Kullanarak bir ileti gönderdiğimde <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve kullanılacak sertifikayı belirttiğinizde, "geçersiz sertifika" iletisi alıyorum. Bu Nasıl yaparım? düzeltilsin mi?

Y **:** Sertifika modunda yerel makine sertifika deposu kullanamazsınız. Sertifika ek bileşenini kullanarak sertifikayı makine sertifika deposundan geçerli kullanıcı deposuna kopyalamanız gerekir. Sertifika ek bileşenini almak için:

1. **Başlat**' a tıklayın, **Çalıştır**' ı seçin `mmc` ve ardından **Tamam**' a tıklayın.

2. **Microsoft Yönetim Konsolu**'nda **Dosya** menüsünü açın ve **ek bileşen Ekle/Kaldır**' ı seçin.

3. **Ek bileşen Ekle/Kaldır** Iletişim kutusunda **Ekle** düğmesine tıklayın.

4. **Tek başına ek bileşen Ekle** Iletişim kutusunda Sertifikalar ' ı seçin ve **Ekle**' ye tıklayın.

5. **Sertifikalar** ek bileşeni iletişim kutusunda **Kullanıcı hesabım** ' ı seçin ve **son**' a tıklayın.

6. Ardından, önceki adımları kullanarak ikinci bir sertifika ek bileşeni ekleyin, ancak bu kez **bilgisayar hesabı** ' nı seçin ve **İleri**' ye tıklayın.

7. **Yerel Bilgisayar** öğesini seçip **Tamamla** öğesini tıklatın. Artık makine sertifika deposundaki sertifikaları mevcut Kullanıcı deposuna sürükleyip bırakabilirsiniz.

**S:** Hizmetlerim çalışma grubu modundaki başka bir bilgisayardaki bir kuyruktan okurken "erişim engellendi" özel durumu alıyorum.

Y **:** Çalışma grubu modunda, uzak bir uygulamanın sıraya erişim kazanması için, uygulamanın sıraya erişim izni olması gerekir. Kuyruğun erişim denetim listesine (ACL) "anonim oturum açma" ekleyin ve okuma izni verin.

**S:** Bir ağ hizmeti istemcisi (veya etki alanı hesabı olmayan herhangi bir istemci) sıraya alınmış bir ileti gönderdiğinde, gönderme işlemi geçersiz bir sertifika ile başarısız olur. Bu Nasıl yaparım? düzeltilsin mi?

Y **:** Bağlama yapılandırmasını denetleyin. İletiyi imzalamak için varsayılan bağlamada MSMQ aktarım güvenliği açıktır. Kapatın.

### <a name="remote-transacted-receives"></a>Uzaktan Işlem temelli alır

**S:** A makinesinde bir kuyruk olduğunda ve B makinesindeki bir sıradan iletileri okuyan bir WCF hizmeti (uzaktan işlem temelli alma senaryosu) olduğunda İletiler kuyruktan okunmaz. İzleme bilgileri, alma Işleminin "Işlem içeri aktarılamıyor" iletisiyle başarısız olduğunu gösterir. Bunu onarmak için ne yapabilirim?

Y **:** Bunun üç olası nedeni vardır:

- Etki alanı modundaysanız, uzaktan işlem alma, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ erişimi gerektirir. Bu ayarı, **Bileşen Ekle/Kaldır**'ı kullanarak etkinleştirebilirsiniz.

  ![Ağ DTC erişimini etkinleştirmeyi gösteren ekran görüntüsü.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- İşlem yöneticisiyle iletişim kurmak için kimlik doğrulama modunu denetleyin. Çalışma grubu modundaysanız, "kimlik doğrulaması gerekli değil" seçilmelidir. Etki alanı modundaysanız, "karşılıklı kimlik doğrulaması gerekir" seçilmelidir.

  ![XA işlemlerini etkinleştirme](media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-FB0B-4c5b-AFAC-75f8860d2bb0")

- MSDTC 'nin **Internet bağlantısı güvenlik duvarı** ayarları 'ndaki özel durumlar listesinde olduğundan emin olun.

- Windows Vista kullandığınızdan emin olun. Windows Vista 'da MSMQ, uzaktan işlenen okumayı destekler. Önceki Windows sürümlerindeki MSMQ, uzaktan işlenen okumayı desteklemez.

**S:** Kuyruktan okuma hizmeti bir ağ hizmeti olduğunda (örneğin, bir Web ana bilgisayarında), kuyruktan okurken neden bir erişim reddedildi özel durumu ortaya aldım?

Y **:** Ağ hizmetinin kuyruktan okuyabağlanabildiğinden emin olmak için kuyruk ACL 'sine ağ hizmeti okuma erişimi eklenmelidir.

**S:** MSMQ etkinleştirme hizmetini, uzak bir makinedeki bir kuyruktaki iletilere göre uygulamaları etkinleştirmek için kullanabilir miyim?

**Y:** Evet. Bunu yapmak için MSMQ etkinleştirme hizmetini bir ağ hizmeti olarak çalışacak şekilde yapılandırmanız ve uzak makinedeki sıraya ağ hizmeti erişimi eklemeniz gerekir.

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>ReceiveContext etkin özel MSMQ bağlamaları kullanma

Etkin bir MSMQ bağlama kullanılırken <xref:System.ServiceModel.Channels.ReceiveContext> , gelen bir iletiyi işlemek bir iş parçacığı havuzu iş parçacığı kullanır çünkü yerel MSMQ, zaman uyumsuz alma işlemleri için g/ç tamamlamayı desteklemez <xref:System.ServiceModel.Channels.ReceiveContext> . Bunun nedeni, bu tür bir iletinin işlenmesi için iç işlemleri kullanması <xref:System.ServiceModel.Channels.ReceiveContext> ve MSMQ zaman uyumsuz işlemeyi desteklemez. Bu sorunu geçici olarak çözmek için, <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> zaman uyumlu işlemeyi zorlamak veya 1 olarak ayarlamak üzere uç noktaya ekleyebilirsiniz <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> .
