---
title: "Kuyruğa Alınan İletilerde Sorun Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a23dd402cdc12cd20ce7273a96df056aeda71ceb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="troubleshooting-queued-messaging"></a>Kuyruğa Alınan İletilerde Sorun Giderme
Bu bölüm yaygın sorular ve sorun giderme Yardımı kuyruklarda kullanma içerir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="common-questions"></a>Sık sorulan sorular  
 **S:** kullandım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Beta 1 ve MSMQ düzeltmesinin yüklü. Düzeltmeyi kaldırmak gerekiyor mu?  
  
 **Y:** Evet. Bu düzeltme artık desteklenmiyor. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Şimdi MSMQ üzerinde bir düzeltme gereksinimi çalışır.  
  
 **S:** MSMQ için iki bağlamaları vardır: <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Ne kullanmalıyım ve ne zaman?  
  
 **Y:** kullanmak <xref:System.ServiceModel.NetMsmqBinding> MSMQ iki arasında kuyruğa alınan iletişim için bir taşıma olarak kullanmak istediğiniz zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar. Kullanmak <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> varolan MSMQ uygulamalarının yeni iletişim kurması için kullanmak istediğiniz zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
 **S:** kullanmak için MSMQ yükseltme zorunda <xref:System.ServiceModel.NetMsmqBinding> ve `MsmqIntegration` bağlamaları?  
  
 **C:** Hayır. MSMQ 3.0 ile çalışmak belirtilmemiştir [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. MSMQ 4. 0'ye yükseltme yaptığınızda bağlamaları belirli özellikleri kullanılabilir duruma [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **S:** hangi özelliklerini <xref:System.ServiceModel.NetMsmqBinding> ve <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bağlamaları MSMQ 4.0 ancak içinde değil MSMQ 3.0 kullanılabilir?  
  
 **Y:** MSMQ 4.0 ancak içinde değil MSMQ 3.0 aşağıdaki özellikler mevcuttur:  
  
-   Özel sahipsiz sırayı yalnızca MSMQ 4.0 üzerinde desteklenir.  
  
-   MSMQ 3.0 ve 4.0 zarar iletileri farklı şekilde işler.  
  
-   Yalnızca MSMQ 4.0 uzaktan hizmetteki okuma destekler.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Vista, Windows Server 2003 ve Windows XP'de kuyruğa alma özelliği farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **S:** MSMQ 3.0 kuyruğa alınan iletişim ve MSMQ 4.0 bir tarafındaki diğer tarafındaki kullanabilir miyim?  
  
 **Y:** Evet.  
  
 **S:** varolan MSMQ uygulamaları ile yeni tümleştirme istediğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler veya sunucular. İki tarafı da my MSMQ altyapı yükseltme gerekiyor mu?  
  
 **C:** Hayır. Her iki tarafında MSMQ 4. 0'için yükseltme gerekmez.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu bölüm yaygın sorun giderme sorunlarını yanıtlarını içerir. Sınırlamalar bilinen bazı sorunlar Sürüm Notları'nda da açıklanmaktadır.  
  
 **S:** özel sıra kullanmak çalışıyorum ve şu özel durum alın: `System.InvalidOperationException`: URL geçersiz. Sıra için URL '$' karakterini içeremez. Özel bir sıra adreslemek için.MSMQ://machine/private/queueName sözdizimini kullanın.  
  
 **Y:** sıraya Tekdüzen Kaynak Tanımlayıcısı (URI) yapılandırma ve kodu gözden geçirin. "$" Karakterini URI'de kullanmayın. Örneğin, OrdersQueue adlı özel bir sıra adreslemek için URI net.msmq://localhost/private/ordersQueue belirtin.  
  
 **S:** çağırma `ServiceHost.Open()` sıraya alınan Uygulamam üzerinde aşağıdaki özel durum oluşturur: `System.ArgumentException`: taban adresi bir URI sorgu dizesi içeremez. Neden?  
  
 **Y:** sıranın URI, yapılandırma dosyanızı ve kodunuzu denetleyin. MSMQ kuyrukları kullanımını desteklerken '?' karakteri, URI bir dize sorgusu başlangıcı olarak bu karakteri yorumlama. Bu sorunu önlemek için içermeyen sıra adları kullanın. '?' karakteri.  
  
 **S:** My gönderme başarılı oldu ancak hizmet işlemi alıcı çağrılır. Neden?  
  
 **Y:** yanıt belirlemek için aşağıdaki denetim listesinde çalışma:  
  
-   İşlem sırası gereksinimleri belirtilen çıkışların ile uyumlu olduğundan emin olun. Aşağıdaki ilkeleri dikkat edin:  
  
    -   Dayanıklı iletileri (veri birimleri ve oturumları) güvence "tam bir kez ile" gönderebilirsiniz (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) yalnızca bir işlem sırası için.  
  
    -   "Tam bir kez" çıkışların yalnızca oturumlarıyla gönderebilirsiniz.  
  
    -   Bir işlem, işlem sıradan bir oturumda ileti almak için gereklidir.  
  
    -   Geçici veya dayanıklı iletilerle (yalnızca veri birimleri) hiçbir garanti vermediğini gönderip alabilir (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) yalnızca işlemsel olmayan bir sıraya için.  
  
-   Sahipsiz Sıra denetleyin. İletilerin bulursanız, neden bunlar teslim edilmeyen belirler.  
  
-   Bağlantı veya sorunları adresleme giden sıralarının denetleyin.  
  
 **S:** özel sahipsiz sırayı belirtilen, ancak gönderen uygulama başlattığınızda, sahipsiz sıra bulunamadı bir özel durum almak veya gönderen uygulama sahipsiz sıraya iznine sahip. Bunun nedeni nedir?  
  
 **Y:** özel sahipsiz sırayı URI ilk segment, örneğin, net.msmq://localhost/private/myAppdead-letter sırası "localhost" veya bilgisayar adı içermelidir.  
  
 **S:** özel sahipsiz sırayı tanımlamak her zaman gereklidir veya varsayılan sahipsiz sırayı yok?  
  
 **Y:** güvence "tam bir kez" varsa (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), ve özel bir sahipsiz sırayı belirtmezseniz, sistem genelinde işleme uygun eski ileti sırası varsayılandır.  
  
 Çıkışların none ise (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), varsayılan bir atılacak işlev sonra.  
  
 **S:** SvcHost.Open bir iletiyle üzerinde "EndpointListener gereksinimleri olamaz yerine getirilmesi tarafından ListenerFactory" Benim hizmet atar. Neden?  
  
 BİR. Hizmet sözleşmesi denetleyin. Put unutmuş "IsOneWay =`true`" tüm hizmet işlemleri üzerinde. Kuyruklar, yalnızca tek yönlü hizmet işlemleri destekler.  
  
 **S:** kuyrukta iletileri vardır, ancak hiçbir hizmet işlemi çağrılır. Sorun nedir?  
  
 **Y:** hizmet ana bilgisayarı hatalı olmadığını belirleyin. İzleme sırasında bakıyorsanız ya da uygulama denetleyebilirsiniz `IErrorHandler`. Zararlı bir ileti algılanırsa, varsayılan olarak, hizmet ana bilgisayar hatası.  
  
 **S:** kuyrukta iletileri vardır, ancak Web barındırılan sıraya alınan Hizmetim etkinleştirilmediğini. Neden?  
  
 **Y:** izinleri en yaygın nedenidir.  
  
1.  Emin `NetMsmqActivator` işlem çalıştığından ve kimliğini `NetMsmqActivator` işlemi okuma verilir ve sıranın izninin arama.  
  
2.  Varsa `NetMsmqActivator` olduğundan emin kuyrukları uzak makinede izleme, `NetMsmqActivator` kısıtlı bir belirteç altında çalışmaz. Çalıştırmak için `NetMsmqActivator` Kısıtlanmamış belirteci ile:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Güvenlikle ilgili Web konağı sorunlarını başvurmak için: [sıraya alınmış bir uygulamayı Web'de barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **S:** en kolay yolu erişim oturumlarına nedir?  
  
 **Y:** Ayarla otomatik tamamlama =`true` son karşılık gelen işlemi oturumda ileti ve otomatik tamamlama ayarlayın =`false` tüm kalan hizmet işlemleri üzerinde.  
  
 **S:** MSMQ hakkında sık sorulan soruların yanıtlarını nereden bulabilirim?  
  
 **Y:** [!INCLUDE[crabout](../../../../includes/crabout-md.md)] MSMQ bkz [Microsoft Message Queuing](http://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **S:** Hizmetim neden throw bir `ProtocolException` içeren bir sıra okunurken zaman oturum sıradaki iletiler ve veri birimi sıradaki iletiler?  
  
 **Y:** şekilde sıralı oturum iletilerindeki temel fark yoktur ve sıraya alınan veri birimi iletileri oluşur. Bu nedenle, sıraya alınan oturum ileti okumak için bekleniyor bir hizmet sıraya alınan veri birimi iletisini alamaz ve sıraya alınan veri birimi ileti okumak bekleniyor hizmet oturumu ileti alamıyor. İki tür ileti aynı sırasından okuma girişimi şu özel durum oluşturur:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Özel herhangi bir teslim edilemeyen sıra yanı sıra sistem sahipsiz sırayı ise bu sorun için özellikle uygulanmadıkça bir uygulama hem de oturum sıradaki iletiler ve aynı bilgisayardan veri birimi iletiler gönderir. Bir ileti başarıyla gönderilemiyor, sahipsiz sıraya taşınır. Bu koşullar altında oturum ve veri birimi iletileri sahipsiz sıraya olması mümkündür. İki tür çalışma zamanında ileti kuyruktan okunurken ayırmak için bir yolu yoktur, bu nedenle, uygulamaları her ikisi de oturum sıradaki iletiler ve veri birimi iletiler aynı bilgisayardan göndermemelisiniz.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>MSMQ tümleştirme: Belirli sorun giderme  
 **S:** bir ileti gönderirken ya da hizmet konağı açtığınızda, düzeni yanlış belirten bir hata alın. Neden?  
  
 **Y:** MSMQ tümleştirme bağlama kullandığınızda, msmq.formatname şeması kullanması gerekir. Örneğin, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Ancak özel sahipsiz sırayı belirttiğinizde, net.msmq şeması kullanması gerekir.  
  
 **S:** ne zaman bir genel veya özel biçim adı kullanın ve hizmet ana bilgisayarı açmak [!INCLUDE[wv](../../../../includes/wv-md.md)], bir hata alıyorsunuz. Neden?  
  
 **Y:** [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tümleştirme kanalda [!INCLUDE[wv](../../../../includes/wv-md.md)] zehirli ileti işleme için ana uygulama sıra için bir alt sırası açıldı durumunda olup olmadığını kontrol eder. Alt sıra adı URI dinleyiciye geçirilen msmq.formatname türetilir. MSMQ alt kuyruk adı yalnızca doğrudan biçim adını olabilir. Bu nedenle, hata görürsünüz. Sıranın URI için doğrudan biçim adını değiştirin.  
  
 **S:** bir ileti bir MSMQ uygulamasından alırken, ileti sıraya bulunur ve alıcı tarafından okunamaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama. Neden?  
  
 **Y:** ileti Gövde sahip olup olmadığını denetleyin. İleti yok gövde sahipse, MSMQ tümleştirme kanalı iletisini yok sayıyor. Uygulama `IErrorHandler` özel durumları bildirilmesini ve izlemeleri denetleyin.  
  
### <a name="security-related-troubleshooting"></a>Güvenlikle ilgili sorun giderme  
 **S:** çalışma grubu modunda varsayılan bağlama kullanan örnek çalıştırdığınızda, iletileri gönderilen görünüyor ancak hiçbir zaman alıcı tarafından alınır.  
  
 **Y:** varsayılan olarak, Active Directory dizin hizmeti gerektiren bir MSMQ iç sertifika kullanarak iletileri imzalanmıştır. Active Directory kullanılamadığından, çalışma grubu modunda ileti imzalama başarısız olur. Bu nedenle sahipsiz sıraya ileti adlandırıldığını ve "Bozuk imza" gibi hata neden belirtilir.  
  
 Güvenlik devre dışı bırakma geçici bir çözüm değildir. Bu ayarlayarak yapılır <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> çalışma grubu modundayken çalışması için.  
  
 Başka bir çözüm almaktır <xref:System.ServiceModel.MsmqTransportSecurity> gelen <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> özelliği ve ayarlamak <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>ve istemci sertifikasını ayarlayın.  
  
 Henüz MSMQ Active Directory Tümleştirme ile yüklemek için başka bir geçici bir çözüm değildir.  
  
 **S:** varsayılan bağlama ile bir ileti gönderdiğinizde t (aktarım açık güvenliği) Active Directory'de bir kuyruk "İç sertifika bulunamadı" iletisi alıyorum. Bunu nasıl düzeltirim?  
  
 **Y:** bu gönderen için Active Directory'de sertifika yenilenmesi gerekir anlamına gelir. Bunu yapmak için açık **Denetim Masası**, **Yönetimsel Araçlar**, **Bilgisayar Yönetimi**, sağ **MSMQ**, seçip**Özellikleri**. Seçin **kullanıcı sertifikası** sekmesinde **yenileme** düğmesi.  
  
 **S:** ı gönderdiğinizde bir iletiyi kullanarak <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ve kullanmak üzere sertifikayı belirtin, bir "Geçersiz sertifika" iletisi alıyorum. Bunu nasıl düzeltirim?  
  
 **Y:** yerel makine sertifika deposuna sertifika moduyla kullanamazsınız. Sertifikayı makine sertifika deposundan sertifika ek bileşenini kullanarak geçerli kullanıcı deposuna kopyalamak gerekir. Sertifika ek bileşenini almak için:  
  
1.  Tıklatın **Başlat**seçin **çalıştırmak**, türü `mmc`, tıklatıp **Tamam**.  
  
2.  İçinde **Microsoft Yönetim Konsolu**, açık **dosya** menü ve select **Ekle/Kaldır ek bileşenini**.  
  
3.  İçinde **Ekle/Kaldır ek bileşenini** iletişim kutusu, tıklatın **Ekle** düğmesi.  
  
4.  İçinde **tek başına ek bileşen Ekle alanında** iletişim kutusu, select sertifikalar ve tıklatın **Ekle**.  
  
5.  İçinde **sertifikaları** ek bileşenini iletişim kutusunda **kullanıcı hesabım** tıklatıp **son**.  
  
6.  Ardından, ikinci bir Sertifikalar ek bileşeni önceki adımları kullanarak, ancak bu kez seçin eklemek **bilgisayar hesabı** tıklatıp **sonraki**.  
  
7.  Seçin **yerel bilgisayar** tıklatıp **son**. Şimdi sürükleyin ve geçerli kullanıcı deposunda makine sertifika deposundan sertifikaları bırakın.  
  
 **S:** zaman Hizmetim okur çalışma grubu modunda, başka bir bilgisayardaki bir sıradan bir "erişim engellendi" özel alıyorum.  
  
 **Y:** sıra erişmek uzak bir uygulama için çalışma grubu modunda uygulama kuyruğa erişim izni olması gerekir. Sıranın erişim denetim listesi (ACL) "Anonim oturum açma" ekleyin ve bu okuma izni verin.  
  
 **S:** bir ağ hizmeti istemcisi (veya bir etki alanı hesabı olmayan herhangi bir istemci) sıraya alınan ileti gönderdiğinde, geçersiz bir sertifikayla gönderme başarısız. Bunu nasıl düzeltirim?  
  
 **Y:** bağlama yapılandırmasını denetleyin. Varsayılan bağlama için açık MSMQ taşıma güvenliği iletiyi yok. Bilgisayarı kapatın.  
  
### <a name="remote-transacted-receives"></a>İşlem yapılan işlem uzaktan alır  
 **S:** bir sıra makine A'da olduğunda ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] makinede bir kuyruktan iletileri (işlem yapılan işlem uzaktan alma senaryosu) B, iletileri sıradan okunamıyor okur hizmet. Bilgi izleme iletisi "işlem aktarılamıyor ile." alma başarısız gösterir Bu sorunu gidermek için ne yapabilirim?  
  
 **Y:** bu üç olası nedeni vardır:  
  
-   Etki alanı modunda olduğundan, işlem yapılan işlem uzaktan alma Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) ağ erişimi gerektiriyor. Bu kullanarak etkinleştirin **Bileşenlerini Ekle/Kaldır**.  
  
     ![Ağ DTC Erişimi'ni etkinleştirme](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   İşlem Yöneticisi ile iletişim için kimlik doğrulama modu denetleyin. Çalışma grubu modunda varsa, "Gereken kimlik doğrulama yok" seçilmesi gerekir. Etki alanı modunda varsa, "Gerekli karşılıklı kimlik doğrulaması" seçilmelidir.  
  
     ![XA işlemleri etkinleştirme](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   MSDTC özel durumlar listesinde olduğundan emin olun **Internet Bağlantısı Güvenlik Duvarı** ayarlar.  
  
-   Kullandığınızdan emin olun [!INCLUDE[wv](../../../../includes/wv-md.md)]. MSMQ üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] uzaktan hizmetteki okuma destekler. Önceki Windows sürümlerinde MSMQ Uzaktan hizmetteki okuma desteklemez.  
  
 **S:** sıradan okuma hizmeti bir ağ hizmeti, örneğin, bir Web ana bilgisayar, bir erişim reddedildi özel neden alabilirim sıradan okunurken tetiklenir?  
  
 **Y:** ağ hizmeti okuma erişimi eklenmelidir, kuyruğa ACL bir ağ hizmeti sıradan okuduğunuzdan emin olun.  
  
 **S:** MSMQ Etkinleştirme hizmeti uzak makinede bir sıradaki iletiler göre uygulamaları etkinleştirmek için kullanabilir miyim?  
  
 **Y:** Evet. Bunu yapmak için bir ağ hizmeti olarak çalıştırılmak için MSMQ Etkinleştirme hizmeti yapılandırma ve ağ hizmeti erişim sıranın uzak makinede ekleyin.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>ReceiveContext etkinleştirilmiş ile özel MSMQ bağlamaları kullanma  
 Özel bir MSMQ bağlama ile kullanırken <xref:System.ServiceModel.Channels.ReceiveContext> etkin bir gelen iletiyi işlemeyi kullanacağınız bir iş parçacığı havuzu iş parçacığı yerel MSMQ için g/ç tamamlama desteklemediği için zaman uyumsuz <xref:System.ServiceModel.Channels.ReceiveContext> alır. Bu tür bir ileti işlenirken iç işlemler için kullanan olmasıdır <xref:System.ServiceModel.Channels.ReceiveContext> ve MSMQ zaman uyumsuz işleme desteklemez. Ekleyebileceğiniz bu sorunu çözmek için bir <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> ayarlayın veya zaman uyumlu zorlamak için uç nokta işlerken <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 1.
