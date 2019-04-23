---
title: Kuyruğa Alınan İletilerde Sorun Giderme
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: c85b0701c870fe2b4a3c11dc384e890e1ed001dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977294"
---
# <a name="troubleshooting-queued-messaging"></a>Kuyruğa Alınan İletilerde Sorun Giderme
Bu bölüm, yaygın sorular ve sorun giderme Yardımı için sıralar kullanarak Windows Communication Foundation (WCF) içerir.  
  
## <a name="common-questions"></a>Sık sorulan sorular  
 **S:** WCF Beta 1 kullandım ve MSMQ düzeltme yüklü. Düzeltmeyi kaldırmak gerekiyor mu?  
  
 **Y:** Evet. Bu düzeltme artık desteklenmiyor. WCF MSMQ üzerinde bir düzeltme gereksinimi şimdi çalışıyor.  
  
 **S:** MSMQ için iki bağlaması vardır: <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Ne kullanmalıyım ve ne zaman?  
  
 **Y:** Kullanma <xref:System.ServiceModel.NetMsmqBinding> MSMQ iki WCF uygulamaları arasındaki kuyruğa alınan iletişim için bir taşıma olarak kullanmak istediğinizde. Kullanma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> yeni WCF uygulamalarla iletişim kurmak için MSMQ uygulamalara kullanmak istediğinizde.  
  
 **S:** Kullanmak için MSMQ yükseltmek zorunda <xref:System.ServiceModel.NetMsmqBinding> ve `MsmqIntegration` bağlamaları?  
  
 **Y:** Hayır. Üzerinde MSMQ 3.0 ile belirtilmemiştir çalışmanıza [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. MSMQ 4. 0'e yükselttiğinizde bağlamaları belirli özellikler kullanılabilir hale gelir [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **S:** Hangi özellikleri <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bağlamaları MSMQ 4.0 ancak içinde olmayan MSMQ 3.0 kullanılabilir?  
  
 **Y:** MSMQ 4.0 ancak içinde olmayan MSMQ 3.0, aşağıdaki özellikler kullanılabilir:  
  
-   Özel eski ileti sırası, yalnızca MSMQ 4.0 desteklenir.  
  
-   MSMQ 3.0 ve 4.0 zehirli iletilerin farklı şekilde işler.  
  
-   Yalnızca MSMQ 4.0 uzaktan hizmetteki okuma destekler.  
  
 Daha fazla bilgi için [Windows Vista, Windows Server 2003 ve Windows XP sıraya alma özelliği arasındaki farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **S:** Kuyruğa alınan iletişim ve MSMQ 4. 0'ın bir tarafında diğer tarafta MSMQ 3.0 kullanabilir miyim?  
  
 **Y:** Evet.  
  
 **S:** MSMQ uygulamalara yeni WCF istemciler veya sunucular ile tümleştirmek istediğiniz. Her iki tarafında bir MSMQ altyapımı yükseltme gerekiyor mu?  
  
 **Y:** Hayır. MSMQ 4. 0'için iki tarafında yükseltme gerekmez.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu bölümde, en yaygın sorunlarını giderme yanıtlarını içerir. Bilinen sınırlamalar bazı sorunlar da bu sürüm notlarında açıklanmaktadır.  
  
 **S:** Özel bir kuyruk kullanın yapmaya çalışıyorum ve şu özel durum alıyorum: `System.InvalidOperationException`: URL geçersiz. Kuyruk URL'si, '$' karakterini içeremez. Söz dizimi içinde.MSMQ://machine/private/queueName özel sıra ele almak için kullanın.  
  
 **Y:** ' % S'sıra Tekdüzen Kaynak Tanımlayıcısı (URI) yapılandırma ve kodu gözden geçirin. URI'de "$" karakterini kullanmayın. Örneğin, OrdersQueue adlı özel bir sıra adreslemek için net.msmq://localhost/private/ordersQueue URI belirtin.  
  
 **S:** Çağırma `ServiceHost.Open()` sıraya alınan uygulamamı şu özel durum oluşturur: `System.ArgumentException`: Temel adres bir URI sorgu dizesi içeremez. Neden?  
  
 **Y:** Sıranın URI yapılandırma dosyanızdaki ve kodunuzda denetleyin. MSMQ kuyruk kullanımını desteklerken '?' karakteri, bir URI'leri bu karakteri bir dize sorgusuna başlangıcı olarak yorumlar. Bu sorunu önlemek için içermeyen kuyruk adları kullanın. '?' karakteri.  
  
 **S:** My gönderme başarılı oldu, ancak hiçbir hizmet işlemi alıcıda çağrılır. Neden?  
  
 **Y:** Yanıt belirlemek için aşağıdaki denetim listesinde çalışır:  
  
-   İşlem sırası gereksinimleri belirtilen konu ile uyumlu olduğundan emin olun. Aşağıdaki ilkeleri göz önünde bulundurun:  
  
    -   Dayanıklı ileti (veri birimleri ve oturumları) Güvenceleri "tam bir kez ile" gönderebilirsiniz (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) yalnızca bir işlem kuyruğu için.  
  
    -   Yalnızca "tam bir kez" Güvenceleri oturumları gönderebilirsiniz.  
  
    -   Bir işlem, bir işlem kuyruktan bir oturumda ileti alma için gereklidir.  
  
    -   Geçici veya kalıcı iletileri (yalnızca veri birimi) ile hiçbir şekilde gönderip alabilir (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) yalnızca bir işlem olmayan kuyruğu için.  
  
-   Sahipsiz sırayı kontrol edin. İletilerin bulursanız, neden, teslim edilmeyen belirleyin.  
  
-   Giden sıralar bağlantı veya sorunlarını ele alan kontrol edin.  
  
 **S:** Özel bir eski ileti sırası belirtilen, ancak ı gönderen uygulamasını başlattığınızda, eski ileti sırası bulunamadı bir özel durum alabilir miyim veya gönderen uygulamaya sahip eski ileti sırası izni yok. Bunun nedeni nedir?  
  
 **Y:** Özel eski ileti sırası URI, ilk segment, örneğin, net.msmq://localhost/private/myAppdead-letter kuyruk "localhost" veya bilgisayar adını içermelidir.  
  
 **S:** Özel bir sahipsiz sırayı tanımlamak her zaman gereklidir veya varsayılan eski ileti sırası yok?  
  
 **Y:** "Kesinlikle bir kerelik" Güvenceleri varsa (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), ve özel bir eski ileti sırası belirtmezseniz, sistem genelinde işlem eski ileti sırası varsayılandır.  
  
 Güvenceleri hiçbiri varsa (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), sonra atılacak işlevselliği varsayılandır.  
  
 **S:** Hizmetimi SvcHost.Open üzerinde bir ileti "EndpointListener gereksinimleri karşılanamıyor tarafından ListenerFactory" ile oluşturur. Neden?  
  
 A. Hizmet sözleşmeniz denetleyin. Put kaldırmayı unutmuş olabilirsiniz "IsOneWay =`true`" hizmet işlemleri üzerinde. Kuyruklar yalnızca tek yönlü hizmet işlemleri destekler.  
  
 **S:** Kuyrukta ileti vardır, ancak hiçbir hizmet işlemi çağrılır. Sorun nedir?  
  
 **Y:** Hizmet ana hatalı durumunda belirleyin. İzleme arama veya uygulama denetleyebilirsiniz `IErrorHandler`. Zehirli ileti algılanırsa varsayılan olarak, hizmet ana bilgisayar hatası.  
  
 **S:** Kuyrukta ileti vardır, ancak Web barındırılan sıraya alınan Hizmetimi etkinleştirilmemiş. Neden?  
  
 **Y:** En yaygın nedeni izinlerdir.  
  
1. Emin `NetMsmqActivator` işlemi çalışıyor ve kimliğini `NetMsmqActivator` işlemi okuma verilir ve ara sıra izni.  
  
2. Varsa `NetMsmqActivator` olduğundan emin uzak makinede Kuyrukları İzleme, `NetMsmqActivator` kısıtlı bir belirteç altında çalışmaz. Çalıştırılacak `NetMsmqActivator` sınırsız bir belirteç ile:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Güvenlikle ilgili Web ana bilgisayar sorunları için bakın: [Sıraya alınan bir uygulamayı Web'de barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **S:** Erişim oturumları için en kolay yolu nedir?  
  
 **Y:** Otomatik Tamamlama ayarlamak =`true` son karşılık gelen işlemi bir oturumda ileti ve otomatik tamamlama ayarlayın =`false` tüm kalan hizmet işlemleri üzerinde.  
  
 **S:** MSMQ hakkında sık sorulan soruların yanıtlarını nerede bulabilirim?  
  
 **Y:** MSMQ hakkında daha fazla bilgi için bkz: [Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **S:** Hizmetimi neden throw bir `ProtocolException` ne zaman, her ikisini de içeren bir sıra okunurken oturumu sıradaki iletiler ve veri birimi sıradaki iletiler?  
  
 **Y:** Sıralı şekilde oturum iletileri temel bir fark yoktur ve sıraya alınan bir veri birimi iletileri oluşur. Bu nedenle, bir kuyruğa alınmış veri birimi ileti kuyruğa alınmış oturum ileti okumak için bekleniyor bir hizmet alamaz ve sıraya alınan bir veri birimi ileti okumak beklenerek bir hizmete bir oturum ileti alamıyor. Her iki türdeki iletileri aynı kuyruktan okunmaya çalışılırken aşağıdaki özel durum oluşturur:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Tüm özel eski ileti sırası yanı sıra sistem eski ileti sırası ise bu konuda özellikle maruz uygulama hem de oturum sıradaki iletiler ve aynı bilgisayardan veri birimi iletileri kuyruğa gönderir. Bir ileti başarıyla gönderilemiyor, eski ileti sırası için taşınır. Bu koşullar altında hem oturum hem de veri birimi iletileri teslim edilemeyen sırada olması mümkündür. İki tür zamanında ileti kuyruktan okurken ayırmak için bir yolu yoktur, bu nedenle, uygulamaların hem de oturum sıradaki iletiler ve aynı bilgisayardan veri birimi iletileri kuyruğa göndermemelidir.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>MSMQ tümleştirme: Belirli sorun giderme  
 **S:** Ben bir ileti gönderirken ya da hizmet ana bilgisayarı açtığımda, düzeni yanlış olduğunu belirten bir hata alıyorum. Neden?  
  
 **Y:** MSMQ tümleştirme bağlama kullandığınızda msmq.formatname şeması kullanması gerekir. Örneğin, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Ancak özel eski ileti sırası belirttiğinizde, net.msmq şeması kullanması gerekir.  
  
 **S:** Ne zaman bir genel veya özel biçim adı kullanın ve hizmet ana bilgisayarı açmak [!INCLUDE[wv](../../../../includes/wv-md.md)], bir hata alıyorum. Neden?  
  
 **Y:** WCF tümleştirmesi kanalı [!INCLUDE[wv](../../../../includes/wv-md.md)] zehirli ileti işleme için ana uygulama sıra için bir alt kuyruk açılabilir durumunda olup olmadığını kontrol eder. Alt kuyruk adı URI dinleyiciye geçirilen bir msmq.formatname türetilir. MSMQ alt kuyruk adı yalnızca bir doğrudan biçim adı olabilir. Bu nedenle, bir hata görürsünüz. Sıranın URI için doğrudan biçim adını değiştirin.  
  
 **S:** Bir MSMQ uygulamasından bir ileti alındığında, ileti kuyrukta yer alan ve alıcı WCF uygulama tarafından okunamaz. Neden?  
  
 **Y:** İleti gövde olup olmadığını denetleyin. İleti gövde olmadan sahipse, MSMQ tümleştirme kanal iletisi yok sayar. Uygulama `IErrorHandler` özel durumları bildirilmesi ve izlemeler denetleyin.  
  
### <a name="security-related-troubleshooting"></a>Güvenlikle ilgili sorun giderme  
 **S:** Çalışma grubu modunda varsayılan bağlama kullanan örnek çalıştırabilir, iletileri gönderilebilmesi için görünüyor ancak hiçbir zaman alıcı tarafından alınır.  
  
 **Y:** Varsayılan olarak, Active Directory dizin hizmeti gerektiren bir MSMQ iç sertifika kullanarak iletileri imzalanmıştır. Active Directory kullanılabilir değil, çünkü çalışma grubu modunda ileti imzalama başarısız olur. Bu nedenle eski ileti sırası iletiyi gölünüzdeki ve "Hatalı imza" gibi hata neden belirtilir.  
  
 Geçici çözüm, güvenliğin devre dışı açmaktır. Bu ayarı gerçekleştirilir <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> çalışma grubu modunda çalışması için.  
  
 Başka bir çözüm elde etmektir <xref:System.ServiceModel.MsmqTransportSecurity> gelen <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> özelliği ve değerini <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, istemci sertifikasını ayarlayın.  
  
 Henüz MSMQ Active Directory Tümleştirmesi ile yüklemek için başka bir çözüm olabilir.  
  
 **S:** Varsayılan bağlama ile bir iletiyi gönderdiğinizde miyim (aktarım güvenliği etkinleştirilmiş) bir kuyruk için Active Directory'de bir "İç sertifika bulunamadı" iletisi alıyorum. Bunu nasıl düzeltirim?  
  
 **Y:** Başka bir deyişle, Active Directory'de sertifika gönderen için yenilenmesi gerekir. Bunu yapmak için açık **Denetim Masası**, **Yönetimsel Araçlar**, **Bilgisayar Yönetimi**, sağ **MSMQ**, seçip**Özellikleri**. Seçin **kullanıcı sertifikası** sekmesine **yenileme** düğmesi.  
  
 **S:** Ne zaman gönderebilirim kullanarak bir ileti <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve kullanılacak sertifikayı belirtin, "Geçersiz sertifika" iletisi alıyorum. Bunu nasıl düzeltirim?  
  
 **Y:** Bir yerel makine sertifika deposuna sertifika moduyla kullanamazsınız. Geçerli kullanıcı deposunda sertifika ek bileşenini kullanarak makine sertifika deposundan sertifikayı kopyalamanız gerekir. Sertifika ek bileşenini almak için:  
  
1. Tıklayın **Başlat**seçin **çalıştırma**, türü `mmc`, tıklatıp **Tamam**.  
  
2. İçinde **Microsoft Yönetim Konsolu**açın **dosya** menü ve select **Ekle/Kaldır ek bileşenini**.  
  
3. İçinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklayın **Ekle** düğmesi.  
  
4. İçinde **tek başına ek eklentisi** iletişim kutusu, select sertifikaları ve tıklatın **Ekle**.  
  
5. İçinde **sertifikaları** ek iletişim kutusunda **kullanıcı hesabım** tıklatıp **son**.  
  
6. Ardından, ikinci bir Sertifikalar ek bileşeni önceki adımları kullanarak, ancak bu kez ekleyin **bilgisayar hesabı** tıklatıp **sonraki**.  
  
7. Seçin **yerel bilgisayar** tıklatıp **son**. Artık sürükleyin ve sertifikaları makine sertifika depolama alanından geçerli kullanıcı deposunda bırakın.  
  
 **S:** Çalışma grubu modunda başka bir bilgisayarda bir kuyruktan Hizmetimi okuduğunda, "erişim engellendi" istisna alıyorum.  
  
 **Y:** Kuyruk erişim kazanmak uzak bir uygulama için çalışma grubu modunda uygulama kuyruğa erişim izni olması gerekir. Sıranın erişim denetim listesine (ACL) "Anonim oturum açma" ekleyin ve okuma izni verin.  
  
 **S:** Bir ağ hizmeti istemcisi (veya bir etki alanı hesabı olmayan herhangi bir istemci) bir kuyruğa alınmış ileti gönderdiğinde, gönderme, geçersiz bir sertifika ile başarısız olur. Bunu nasıl düzeltirim?  
  
 **Y:** Bağlama yapılandırmasını denetleyin. Varsayılan bağlama için açık MSMQ taşıma güvenlik ileti oturum yok. Kapatın.  
  
### <a name="remote-transacted-receives"></a>Uzak işlem temelli alır  
 **S:** Bir kuyruk bulunan makineye B (işlem temelli uzak alma senaryosu), bir kuyruktan iletileri okuyan bir ve bir WCF Hizmeti makine, iletileri kuyruktan okunmak yok edilir. Bilgi izleme iletisi "işlem aktarılamıyor." alma başarısız gösterir Bu sorunu gidermek için ne yapabilirim?  
  
 **Y:** Bu üç olası nedeni vardır:  
  
-   Etki alanı modunda iseniz, işlem temelli uzaktan alma Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ erişimi gerekmektedir. Bunu kullanarak etkinleştirmek **Bileşenlerini Ekle/Kaldır**.  
  
     ![Etkinleştirme gösteren ekran görüntüsü DTC ağ erişim.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)  
  
-   İşlem Yöneticisi ile iletişim kurmak için kimlik doğrulama modunu kontrol edin. Çalışma grubu modunda iseniz, "Gerekli kimlik doğrulaması yok" seçilmesi gerekir. Etki alanı modunda iseniz, "Gerekli karşılıklı kimlik doğrulaması" seçilmelidir.  
  
     ![XA işlemlerini etkinleştirme](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   MSDTC özel durumlar listesinde olduğundan emin olun **Internet Bağlantısı Güvenlik Duvarı** ayarları.  
  
-   Kullandığınızdan emin olun [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] uzaktan hizmetteki okuma destekler. MSMQ önceki Windows sürümleri üzerinde uzaktan hizmetteki okuma desteklemez.  
  
 **S:** Kuyruktan okuma hizmeti bir ağ hizmeti olduğunda, örneğin, bir Web ana bilgisayar, bir erişim reddedildi özel neden alıyorum kuyruktan okurken oluşturulur?  
  
 **Y:** Ağ hizmeti kuyruktan okuyabilirsiniz emin olmak için ACL kuyruğa ağ hizmeti okuma erişimi eklenmelidir.  
  
 **S:** Uzak makinede sıradaki iletilerin göre uygulamaları etkinleştirmek için MSMQ Etkinleştirme hizmeti kullanabilir miyim?  
  
 **Y:** Evet. Bunu yapmak için bir ağ hizmeti olarak çalıştırmak için MSMQ Etkinleştirme hizmeti yapılandırma ve ağ hizmeti erişimi uzak makinede kuyruğa ekleyin.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>ReceiveContext etkinleştirilmiş ile özel MSMQ bağlamaları kullanma  
 Özel bir MSMQ bağlama ile kullanırken <xref:System.ServiceModel.Channels.ReceiveContext> etkin bir gelen iletiyi işlemeyi kullanacağı bir iş parçacığı havuzu iş parçacığı yerel MSMQ için g/ç tamamlama desteklemediği için zaman uyumsuz <xref:System.ServiceModel.Channels.ReceiveContext> alır. Böyle bir ileti işlenirken iç işlemler için kullanıyor olmasıdır <xref:System.ServiceModel.Channels.ReceiveContext> ve MSMQ zaman uyumsuz işleme desteklemez. Ekleyebileceğiniz bu sorunu çözmek için bir <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> ayarlayın ya da zaman uyumlu zorlamak için uç noktaya işleme <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 1.
