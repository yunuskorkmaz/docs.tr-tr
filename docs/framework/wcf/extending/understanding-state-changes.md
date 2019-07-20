---
title: Durum Değişikliklerini Anlama
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 549620ee5317e68735b392ce35b73c92f2474eab
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363946"
---
# <a name="understanding-state-changes"></a>Durum Değişikliklerini Anlama
Bu konu, kanalların sahip olduğu durumları ve geçişleri, kanal durumlarını yapılandırmak için kullanılan türleri ve bunların nasıl uygulanacağını ele alır.  
  
## <a name="state-machines-and-channels"></a>Durum makineleri ve kanallar  
 Örneğin yuvalar gibi iletişim ile ilgilenen nesneler, genellikle durum geçişleri ağ kaynakları ayırmaya, bağlantı yapmaya veya kabul etmeye, bağlantıları kapatmaya ve iletişimi sonlandırmayla ilişkili olan bir durum makinesi sunar. Kanal durumu makinesi, ilgili nesnenin temel uygulamasını soyutlayan bir iletişim nesnesi durumlarının Tekdüzen bir modelini sağlar. <xref:System.ServiceModel.ICommunicationObject> Arabirim bir durumlar kümesi, durum geçiş yöntemleri ve durum geçiş olayları sağlar. Tüm kanallar, kanal fabrikaları ve kanal dinleyicileri kanal durumu makinesini uygular.  
  
 Durum geçişi gerçekleştirildikten sonra, kapatılan, kapatılan, hatalı, açılan ve açma sinyali bir dış gözlemci oluşur.  
  
 Bu yöntemler Iptal, kapatma ve açma (ve zaman uyumsuz eşdeğerleri) durum geçişlerine neden olur.  
  
 State özelliği şu şekilde tanımlandığı <xref:System.ServiceModel.CommunicationState>şekilde geçerli durumu döndürür:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Idimmunicationobject, CommunicationObject, durumlar ve durum geçişi  
 , Çeşitli özelliklerinin yapılandırılabileceği oluşturulan durumunda başlatılır.<xref:System.ServiceModel.ICommunicationObject> Açık durumda, nesne ileti göndermek ve almak için kullanılabilir ancak özellikleri sabit olarak değerlendirilir. Kapanış durumunda, nesne artık yeni gönderme veya alma isteklerini işleyemez, ancak mevcut isteklerin, kapatma zaman aşımına ulaşılıncaya kadar tamamlanalım olasılığı vardır.  Kurtarılamaz bir hata oluşursa, nesne hata hakkında bilgi için incelenebileceği ve son olarak kapatılan hatalı duruma geçer. Kapalı durumda, nesne aslında durum makinesinin sonuna ulaştı. Bir nesne bir durumdan diğerine geçiş yaptığında önceki bir duruma geri döner.  
  
 Aşağıdaki diyagramda <xref:System.ServiceModel.ICommunicationObject> durumlar ve durum geçişleri gösterilmektedir. Durum geçişleri, üç yöntemden birini çağırarak oluşabilir: İptal edin, açın veya kapatın. Ayrıca, uygulamaya özgü diğer yöntemler çağırılmadan de kaynaklanmış olabilir. İletişim nesnesini açarken veya açtıktan sonra hatanın sonucu olarak hatalı duruma geçme gerçekleşecektir.  
  
 Oluşturulan <xref:System.ServiceModel.ICommunicationObject> durumunda her bir tanesi başlatılır. Bu durumda, bir uygulama, özelliklerini ayarlayarak nesneyi yapılandırabilir. Bir nesne, oluşturulduktan sonra bir durumda olduğunda, bu, sabit olarak değerlendirilir.  
  
 ![Kanal durumu geçişi](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "Channelstatetranitionshighleveldiagram")  
Şekil 1. Idimmunicationobject durum makinesi.  
  
 Windows Communication Foundation (WCF), ve kanal durumu makinesini uygulayan <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ICommunicationObject> adlı bir soyut temel sınıf sağlar. Aşağıdaki grafik, öğesine <xref:System.ServiceModel.Channels.CommunicationObject>özgü değiştirilmiş bir durum diyagramıdır. <xref:System.ServiceModel.ICommunicationObject> Durum makinesine ek olarak, ek <xref:System.ServiceModel.Channels.CommunicationObject> Yöntemler çağrıldığında zamanlamayı gösterir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Şekil 2. Idimmunicationobject durum makinesinin, olaylara ve korunan yöntemlere çağrılar dahil olmak üzere CommunicationObject uygulamasıdır.  
  
### <a name="icommunicationobject-events"></a>Idimmunicationobject olayları  
 <xref:System.ServiceModel.Channels.CommunicationObject>tarafından <xref:System.ServiceModel.ICommunicationObject>tanımlanan beş olayı gösterir. Bu olaylar, durum geçişleri hakkında bildirim almak için iletişim nesnesi kullanılarak kod için tasarlanmıştır. Yukarıdaki Şekil 2 ' de gösterildiği gibi, her bir olay, nesnenin durumu olay tarafından adlandırılan duruma geçtikten sonra tetiklenir. Beş olay `EventHandler` , şöyle tanımlanmış olan türüdür:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 Uygulamada, gönderen <xref:System.ServiceModel.Channels.CommunicationObject> kendisi veya gönderen <xref:System.ServiceModel.Channels.CommunicationObject> olarak oluşturucuya (Oluşturucu aşırı yüklemesi kullanılmışsa) iletilir. <xref:System.ServiceModel.Channels.CommunicationObject> EventArgs parametresi, `e`her zaman `EventArgs.Empty`olur.  
  
### <a name="derived-object-callbacks"></a>Türetilmiş nesne geri çağırmaları  
 Beş olaya ek olarak, <xref:System.ServiceModel.Channels.CommunicationObject> türetilmiş bir nesnenin durum geçişleri gerçekleşmesinden önce ve sonra geri çağrılmasına izin vermek için tasarlanan sekiz korumalı sanal yöntem bildirir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> Ve<xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> yöntemlerinin her biri ile ilişkili üç geri çağırmalar vardır. Örneğin, ve <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> '<xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>a karşılık gelen. İle <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>ilişkili, ,<xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>ve yöntemleridir<xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> .  
  
 Benzer şekilde, <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> yöntemi karşılık gelir. <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>  
  
 ,, Ve<xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> varsayılan bir uygulamasına sahip olmasa da, diğer geri çağırmaların durum makinesi doğruluğu için gerekli olan varsayılan bir uygulamasına sahip olması gerekir. <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType> Bu yöntemleri geçersiz kılarsınız, temel uygulamayı çağırdığınızdan veya doğru şekilde değiştirdiğinizden emin olun.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType><xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> ve ilgili<xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> veolaylarını<xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> harekete geçirme. <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nesne durumunu açık ve kapalı olarak ayarlayıp, ilgili <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> olayları harekete geçirme.  
  
### <a name="state-transition-methods"></a>Durum geçiş yöntemleri  
 <xref:System.ServiceModel.Channels.CommunicationObject>Durdurma, kapatma ve açma uygulamalarını sağlar. Ayrıca, hatalı duruma bir durum geçişine neden olan bir hata yöntemi sağlar. Şekil 2 <xref:System.ServiceModel.ICommunicationObject> ' de, yönteme neden olan yöntemin etiketlendiği her bir geçişe (etiketlenmemiş geçişlerin, son etiketlenmiş geçişe neden olan yöntemin uygulanması içinde yer alan  
  
> [!NOTE]
>  İletişim <xref:System.ServiceModel.Channels.CommunicationObject> durumu Al/ayarlar 'ın tüm uygulamaları iş parçacığı ile eşitlendi.  
  
 Oluşturucu  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>, bir bütün olarak nesneyi oluşturulan durumda bırakarak üç Oluşturucu sağlar. Oluşturucular şu şekilde tanımlanır:  
  
 İlk Oluşturucu, bir nesneyi alan Oluşturucu aşırı yüküne temsilci olarak bulunmayan parametresiz bir oluşturucudur:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Nesne alan Oluşturucu, iletişim nesnesi durumuna erişimi eşitlerken bu parametreyi kilitlenecek nesne olarak kullanır:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Son olarak, üçüncü bir Oluşturucu, <xref:System.ServiceModel.ICommunicationObject> olaylar tetiklendiğinde gönderici bağımsız değişkeni olarak kullanılan ek bir parametre alır.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Önceki iki Oluşturucu göndereni bu olarak ayarlar.  
  
 Yöntemi aç  
  
 Koşul Durum oluşturuldu.  
  
 Koşul sonrası: Durum açıldı veya hatalı. Bir özel durum oluşturabilir.  
  
 Open () yöntemi iletişim nesnesini açmaya çalışır ve durumu açık olarak ayarlar. Bir hatayla karşılaşırsa, durumu hatalı olarak ayarlar.  
  
 Yöntemi önce geçerli durumunun oluşturulduğunu denetler. Geçerli durum açılıyor veya açılırsa, bir <xref:System.InvalidOperationException>oluşturur. Geçerli durum kapanıyor veya kapanırsa, nesne sonlandırılmışsa ve <xref:System.ServiceModel.CommunicationObjectAbortedException> <xref:System.ObjectDisposedException> Aksi takdirde bir oluşturur. Geçerli durum hata oluşturursa, bir <xref:System.ServiceModel.CommunicationObjectFaultedException>oluşturur.  
  
 Ardından, açılan durumu ayarlar ve bu sırayla Onaçýlýþ () (açýlýþ olayını başlatan), OnOpen () ve Onaçılmış () çağırır. Onaçılmış () durumu açıldı olarak ayarlar ve açılan olayı başlatır. Bunlardan herhangi biri bir özel durum oluşturursa, () hatasını () çağırır ve özel durum kabarcığa izin verir. Aşağıdaki diyagramda açık işlem daha ayrıntılı gösterilmektedir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Bir iç iletişim nesnesi açmak gibi özel açık mantığı uygulamak için OnOpen yöntemini geçersiz kılın.  
  
 Close Yöntemi  
  
 Koşul Yok.  
  
 Koşul sonrası: Durum kapalı. Bir özel durum oluşturabilir.  
  
 Close () yöntemi herhangi bir durumda çağrılabilir. Nesneyi normal şekilde kapatmaya çalışır. Bir hata ile karşılaşılırsa, nesneyi sonlandırır. Geçerli durum kapanış veya kapalı ise yöntem hiçbir şey yapmaz. Aksi takdirde, durumu kapanış olarak ayarlar. Özgün durum oluşturuldu, açılıyor veya hata verdi ise, Abort () öğesini çağırır (Aşağıdaki diyagrama bakın). Özgün durum açılırsa, bu sırayla OnClosing () (kapanış olayını başlatan), OnClose () ve OnClosed () çağırır. Bunlardan herhangi biri bir özel durum oluşturursa, Close () Abort () yöntemini çağırır ve özel durum kabarcığa izin verir. OnClosed () durumu kapalı olarak ayarlar ve kapalı olayı başlatır. Aşağıdaki diyagramda, kapatma işlemi daha ayrıntılı gösterilmektedir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO-CloseFlowChartc")  
İç iletişim nesnesini kapatma gibi özel kapatma mantığını uygulamak için OnClose metodunu geçersiz kılın. Uzun süredir engelleyebilen tüm düzgün kapanma mantığı (örneğin, diğer tarafın yanıt vermesi bekleniyor), bir zaman aşımı parametresi aldığı ve Abort () öğesinin bir parçası olarak çağrılmadığı için OnClose () içinde uygulanmalıdır.  
  
 Durdurma  
  
 Koşul Yok.  
Koşul sonrası: Durum kapalı. Bir özel durum oluşturabilir.  
  
 Geçerli durum kapalıysa veya nesne daha önce sonlandırılmışsa, Abort () yöntemi hiçbir şey yapmaz (örneğin, büyük olasılıkla başka bir iş parçacığında yürütme (). Aksi halde, durumu kapatılacak şekilde ayarlar ve OnClosing () (kapanış olayını başlatan), OnAbort () ve OnClosed () Bu sırada (nesne Sonlandırılmakta, kapanmadığı için OnClose çağırmaz) çağırır. OnClosed () durumu kapalı olarak ayarlar ve kapalı olayı başlatır. Bunlardan herhangi biri bir özel durum oluştursa, bu, Iptal etme çağıranına yeniden oluşturulur. OnClosing (), OnClosed () ve OnAbort () uygulamaları engellenmemelidir (örneğin, giriş/çıkış üzerinde). Aşağıdaki diyagramda, durdurma işlemi daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO-AbortFlowChartc")  
Bir iç iletişim nesnesini sonlandırma gibi özel sonlandırma mantığını uygulamak için OnAbort metodunu geçersiz kılın.  
  
 Dayanıklı  
  
 Hata yöntemi, <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ICommunicationObject> arabirimine özeldir ve arabirimin bir parçası değildir. Bu, tamamlanma açısından burada yer alır.  
  
 Koşul Yok.  
  
 Koşul sonrası: Durum hatalı. Bir özel durum oluşturabilir.  
  
 Hata () yöntemi, geçerli durum hata verdi veya kapatılırsa hiçbir şey yapmaz. Aksi takdirde, durumu hatalı olarak ayarlar ve hatalı olayı oluşturan Onkusurlu () öğesini çağırın. Onkusurlu, yeniden oluşturulduğu bir özel durum oluşturursa.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx yöntemleri  
 CommunicationObject, nesne belirli bir durumdaysa özel durum oluşturmak için kullanılabilecek üç korumalı yönteme sahiptir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>durum kapanış, kapatma veya hatalı ise bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>durum oluşturulmadıysa bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>durum açılmadıysa bir özel durum oluşturur.  
  
 Oluşturulan özel durumlar duruma bağlıdır. Aşağıdaki tabloda, bu durumu oluşturan bir ThrowIfXxx çağırarak oluşturulan farklı durumlar ve karşılık gelen özel durum türü gösterilmektedir.  
  
|Durum|Iptal çağrıldı mı?|Özel Durum|  
|-----------|----------------------------|---------------|  
|Oluşturuldu|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açma|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Makta|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Kapatma|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Kapatma|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Closed|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>bir nesnenin önceki ve açık bir Abort çağrısıyla kapatılmış olması durumunda. Nesne üzerinde close çağrısı yaparsanız, bir <xref:System.ObjectDisposedException?displayProperty=nameWithType> oluşturulur.|  
|Closed|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Alındı|Yok|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Zaman Aşımları  
 Tartışıyoruz yöntemlerin birkaçı zaman aşımı parametrelerini alır. Bunlar kapalı, Açık (belirli aşırı yüklemeler ve zaman uyumsuz sürümler), OnClose ve OnOpen. Bu yöntemler uzun işlemlere izin vermek için tasarlanmıştır (örneğin, bir bağlantıyı düzgün bir şekilde kapatırken giriş/çıkış üzerinde engelleme), zaman aşımı parametresi, kesintiye uğramadan önce bu tür işlemlerin ne kadar sürdüğünü gösterir. Bu yöntemlerin herhangi birinin uygulamaları, bu zaman aşımı süresi içinde çağırana döndüğünden emin olmak için sağlanan zaman aşımı değerini kullanmalıdır. Zaman aşımı kullanmayan diğer yöntemlerin uygulamaları uzun işlemler için tasarlanmamıştır ve giriş/çıkış üzerinde engellenmemelidir.  
  
 Özel durum, bir zaman aşımı olmayan Open () ve Close () aşırı yüklemelerdir. Bu, türetilmiş sınıf tarafından sağlanan varsayılan bir zaman aşımı değeri kullanır. <xref:System.ServiceModel.Channels.CommunicationObject>adlı <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> iki korumalı soyut özelliği gösterir ve <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> şöyle tanımlanır:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Türetilmiş bir sınıf, bir zaman aşımı değeri kullanmayan Open () ve Close () aşırı yüklemeleri için varsayılan zaman aşımını sağlamak üzere bu özellikleri uygular. Ardından, Open () ve Close () uygulamaları varsayılan zaman aşımı değerini geçen bir zaman aşımı süresi alan aşırı yüklemeye temsilci sağlar, örneğin:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>Idefaultcommunicationzamanaşımları  
 Bu arabirimin açık, gönder, al ve Kapat için varsayılan zaman aşımı değerlerini sağlamak üzere dört salt okunurdur özelliği vardır. Her uygulama, uygun şekilde varsayılan değerleri edinmekten sorumludur. Kolaylık sağlar ve <xref:System.ServiceModel.Channels.ChannelListenerBase> bu <xref:System.ServiceModel.Channels.ChannelFactoryBase> değerleri 1 dakika için varsayılan olarak yapın.
