---
title: Durum Değişikliklerini Anlama
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: babc62206fc700fe68c2220c4f2cd717cd758d56
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294059"
---
# <a name="understanding-state-changes"></a>Durum Değişikliklerini Anlama

Bu konu, kanalların sahip olduğu durumları ve geçişleri, kanal durumlarını yapılandırmak için kullanılan türleri ve bunların nasıl uygulanacağını ele alır.  
  
## <a name="state-machines-and-channels"></a>Durum makineleri ve kanallar  

 Örneğin yuvalar gibi iletişim ile ilgilenen nesneler, genellikle durum geçişleri ağ kaynakları ayırmaya, bağlantı yapmaya veya kabul etmeye, bağlantıları kapatmaya ve iletişimi sonlandırmayla ilişkili olan bir durum makinesi sunar. Kanal durumu makinesi, ilgili nesnenin temel uygulamasını soyutlayan bir iletişim nesnesi durumlarının Tekdüzen bir modelini sağlar. <xref:System.ServiceModel.ICommunicationObject>Arabirim bir durumlar kümesi, durum geçiş yöntemleri ve durum geçiş olayları sağlar. Tüm kanallar, kanal fabrikaları ve kanal dinleyicileri kanal durumu makinesini uygular.  
  
 Durum geçişi gerçekleştirildikten sonra, kapatılan, kapatılan, hatalı, açılan ve açma sinyali bir dış gözlemci oluşur.  
  
 Bu yöntemler Iptal, kapatma ve açma (ve zaman uyumsuz eşdeğerleri) durum geçişlerine neden olur.  
  
 State özelliği şu şekilde tanımlandığı şekilde geçerli durumu döndürür <xref:System.ServiceModel.CommunicationState> :  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Idimmunicationobject, CommunicationObject, durumlar ve durum geçişi  

 <xref:System.ServiceModel.ICommunicationObject>, Çeşitli özelliklerinin yapılandırılabileceği oluşturulan durumunda başlatılır. Açık durumda, nesne ileti göndermek ve almak için kullanılabilir ancak özellikleri sabit olarak değerlendirilir. Kapanış durumunda, nesne artık yeni gönderme veya alma isteklerini işleyemez, ancak mevcut isteklerin, kapatma zaman aşımına ulaşılıncaya kadar tamamlanalım olasılığı vardır.  Kurtarılamaz bir hata oluşursa, nesne hata hakkında bilgi için incelenebileceği ve son olarak kapatılan hatalı duruma geçer. Kapalı durumda, nesne aslında durum makinesinin sonuna ulaştı. Bir nesne bir durumdan diğerine geçiş yaptığında önceki bir duruma geri döner.  
  
 Aşağıdaki diyagramda <xref:System.ServiceModel.ICommunicationObject> durumlar ve durum geçişleri gösterilmektedir. Durum geçişleri şu üç yöntemden birini çağırarak oluşabilir: Abort, Open veya Close. Ayrıca, uygulamaya özgü diğer yöntemler çağırılmadan de kaynaklanmış olabilir. İletişim nesnesini açarken veya açtıktan sonra hatanın sonucu olarak hatalı duruma geçme gerçekleşecektir.  
  
 <xref:System.ServiceModel.ICommunicationObject>Oluşturulan durumunda her bir tanesi başlatılır. Bu durumda, bir uygulama, özelliklerini ayarlayarak nesneyi yapılandırabilir. Bir nesne, oluşturulduktan sonra bir durumda olduğunda, bu, sabit olarak değerlendirilir.  
  
 ![Kanal durumu geçişinin veri akışı diyagramı.](./media/understanding-state-changes/channel-state-transitions.gif)  
Şekil 1. Idimmunicationobject durum makinesi.  
  
 Windows Communication Foundation (WCF) <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ICommunicationObject> , ve kanal durumu makinesini uygulayan adlı bir soyut temel sınıf sağlar. Aşağıdaki grafik, öğesine özgü değiştirilmiş bir durum diyagramıdır <xref:System.ServiceModel.Channels.CommunicationObject> . Durum makinesine ek olarak <xref:System.ServiceModel.ICommunicationObject> , ek <xref:System.ServiceModel.Channels.CommunicationObject> Yöntemler çağrıldığında zamanlamayı gösterir.  
  
 ![CommunicationObject uygulama durumu değişikliklerinin veri akışı diyagramı.](./media/understanding-state-changes/communicationobject-implementation-state-machine.gif)
Şekil 2. Idimmunicationobject durum makinesinin, olaylara ve korunan yöntemlere çağrılar dahil olmak üzere CommunicationObject uygulamasıdır.  
  
### <a name="icommunicationobject-events"></a>Idimmunicationobject olayları  

 <xref:System.ServiceModel.Channels.CommunicationObject> tarafından tanımlanan beş olayı gösterir <xref:System.ServiceModel.ICommunicationObject> . Bu olaylar, durum geçişleri hakkında bildirim almak için iletişim nesnesi kullanılarak kod için tasarlanmıştır. Yukarıdaki Şekil 2 ' de gösterildiği gibi, her bir olay, nesnenin durumu olay tarafından adlandırılan duruma geçtikten sonra tetiklenir. Beş olay, `EventHandler` şöyle tanımlanmış olan türüdür:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>Uygulamada, gönderen <xref:System.ServiceModel.Channels.CommunicationObject> kendisi veya gönderen olarak <xref:System.ServiceModel.Channels.CommunicationObject> oluşturucuya (Oluşturucu aşırı yüklemesi kullanılmışsa) iletilir. EventArgs parametresi, `e` her zaman olur `EventArgs.Empty` .  
  
### <a name="derived-object-callbacks"></a>Türetilmiş nesne geri çağırmaları  

 Beş olaya ek olarak, <xref:System.ServiceModel.Channels.CommunicationObject> türetilmiş bir nesnenin durum geçişleri gerçekleşmesinden önce ve sonra geri çağrılmasına izin vermek için tasarlanan sekiz korumalı sanal yöntem bildirir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>Ve <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> yöntemlerinin her biri ile ilişkili üç geri çağırmalar vardır. Örneğin, ve ' a karşılık gelen <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> . İle ilişkili <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> ,, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> yöntemleridir.  
  
 Benzer şekilde, <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> yöntemi karşılık gelir <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> .  
  
 , <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType> , Ve <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> varsayılan bir uygulamasına sahip olmasa da, diğer geri çağırmaların durum makinesi doğruluğu için gerekli olan varsayılan bir uygulamasına sahip olması gerekir. Bu yöntemleri geçersiz kılarsınız, temel uygulamayı çağırdığınızdan veya doğru şekilde değiştirdiğinizden emin olun.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType><xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>ve <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> ilgili ve olaylarını harekete geçirme <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> . <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nesne durumunu açık ve kapalı olarak ayarlayıp, ilgili ve olayları harekete geçirme <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> .  
  
### <a name="state-transition-methods"></a>Durum geçiş yöntemleri  

 <xref:System.ServiceModel.Channels.CommunicationObject> Durdurma, kapatma ve açma uygulamalarını sağlar. Ayrıca, hatalı duruma bir durum geçişine neden olan bir hata yöntemi sağlar. Şekil 2 ' <xref:System.ServiceModel.ICommunicationObject> de, yönteme neden olan yöntemin etiketlendiği her bir geçişe (etiketlenmemiş geçişlerin, son etiketlenmiş geçişe neden olan yöntemin uygulanması içinde yer alan  
  
> [!NOTE]
> <xref:System.ServiceModel.Channels.CommunicationObject>İletişim durumu Al/ayarlar 'ın tüm uygulamaları iş parçacığı ile eşitlendi.  
  
 Oluşturucu  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> , bir bütün olarak nesneyi oluşturulan durumda bırakarak üç Oluşturucu sağlar. Oluşturucular şu şekilde tanımlanır:  
  
 İlk Oluşturucu, bir nesneyi alan Oluşturucu aşırı yüküne temsilci olarak bulunmayan parametresiz bir oluşturucudur:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Nesne alan Oluşturucu, iletişim nesnesi durumuna erişimi eşitlerken bu parametreyi kilitlenecek nesne olarak kullanır:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Son olarak, üçüncü bir Oluşturucu, olaylar tetiklendiğinde gönderici bağımsız değişkeni olarak kullanılan ek bir parametre alır <xref:System.ServiceModel.ICommunicationObject> .  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Önceki iki Oluşturucu göndereni bu olarak ayarlar.  
  
 Yöntemi aç  
  
 Önkoşul: durum oluşturuldu.  
  
 Koşul sonrası: durum açıldı veya hata verdi. Bir özel durum oluşturabilir.  
  
 Open () yöntemi iletişim nesnesini açmaya çalışır ve durumu açık olarak ayarlar. Bir hatayla karşılaşırsa, durumu hatalı olarak ayarlar.  
  
 Yöntemi önce geçerli durumunun oluşturulduğunu denetler. Geçerli durum açılıyor veya açılırsa, bir oluşturur <xref:System.InvalidOperationException> . Geçerli durum kapanıyor veya kapanırsa, <xref:System.ServiceModel.CommunicationObjectAbortedException> nesne sonlandırılmışsa ve <xref:System.ObjectDisposedException> Aksi takdirde bir oluşturur. Geçerli durum hata oluşturursa, bir oluşturur <xref:System.ServiceModel.CommunicationObjectFaultedException> .  
  
 Ardından, açılan durumu ayarlar ve bu sırayla Onaçýlýþ () (açýlýþ olayını başlatan), OnOpen () ve Onaçılmış () çağırır. Onaçılmış () durumu açıldı olarak ayarlar ve açılan olayı başlatır. Bunlardan herhangi biri bir özel durum oluşturursa, () hatasını () çağırır ve özel durum kabarcığa izin verir. Aşağıdaki diyagramda açık işlem daha ayrıntılı gösterilmektedir.  
  
 ![ICommunicationObject. Open durum değişikliklerinin veri akışı diyagramı.](./media/understanding-state-changes/ico-open-process-override-onopen.gif)  
Bir iç iletişim nesnesi açmak gibi özel açık mantığı uygulamak için OnOpen yöntemini geçersiz kılın.  
  
 Close Yöntemi  
  
 Ön koşul: yok.  
  
 Koşul sonrası: durum kapalı. Bir özel durum oluşturabilir.  
  
 Close () yöntemi herhangi bir durumda çağrılabilir. Nesneyi normal şekilde kapatmaya çalışır. Bir hata ile karşılaşılırsa, nesneyi sonlandırır. Geçerli durum kapanış veya kapalı ise yöntem hiçbir şey yapmaz. Aksi takdirde, durumu kapanış olarak ayarlar. Özgün durum oluşturuldu, açılıyor veya hata verdi ise, Abort () öğesini çağırır (Aşağıdaki diyagrama bakın). Özgün durum açılırsa, bu sırayla OnClosing () (kapanış olayını başlatan), OnClose () ve OnClosed () çağırır. Bunlardan herhangi biri bir özel durum oluşturursa, Close () Abort () yöntemini çağırır ve özel durum kabarcığa izin verir. OnClosed () durumu kapalı olarak ayarlar ve kapalı olayı başlatır. Aşağıdaki diyagramda, kapatma işlemi daha ayrıntılı gösterilmektedir.  
  
 ![Immunicationobject. Close durum değişikliklerinin veri akışı diyagramı.](./media/understanding-state-changes/ico-close-process-override-onclose.gif)  
İç iletişim nesnesini kapatma gibi özel kapatma mantığını uygulamak için OnClose metodunu geçersiz kılın. Uzun süredir engelleyebilen tüm düzgün kapanma mantığı (örneğin, diğer tarafın yanıt vermesi bekleniyor), bir zaman aşımı parametresi aldığı ve Abort () öğesinin bir parçası olarak çağrılmadığı için OnClose () içinde uygulanmalıdır.  
  
 Durdurma  
  
 Ön koşul: yok.  
Koşul sonrası: durum kapalı. Bir özel durum oluşturabilir.  
  
 Geçerli durum kapalıysa veya nesne daha önce sonlandırılmışsa, Abort () yöntemi hiçbir şey yapmaz (örneğin, büyük olasılıkla başka bir iş parçacığında yürütme (). Aksi halde, durumu kapatılacak şekilde ayarlar ve OnClosing () (kapanış olayını başlatan), OnAbort () ve OnClosed () Bu sırada (nesne Sonlandırılmakta, kapanmadığı için OnClose çağırmaz) çağırır. OnClosed () durumu kapalı olarak ayarlar ve kapalı olayı başlatır. Bunlardan herhangi biri bir özel durum oluştursa, bu, Iptal etme çağıranına yeniden oluşturulur. OnClosing (), OnClosed () ve OnAbort () uygulamaları engellenmemelidir (örneğin, giriş/çıkış üzerinde). Aşağıdaki diyagramda, durdurma işlemi daha ayrıntılı olarak gösterilmiştir.  
  
 ![ICommunicationObject. Abort durum değişikliklerinin veri akışı diyagramı.](./media/understanding-state-changes/ico-abort-process-override-onabort.gif)  
Bir iç iletişim nesnesini sonlandırma gibi özel sonlandırma mantığını uygulamak için OnAbort metodunu geçersiz kılın.  
  
 Dayanıklı  
  
 Hata yöntemi, <xref:System.ServiceModel.Channels.CommunicationObject> arabirimine özeldir ve arabirimin bir parçası değildir <xref:System.ServiceModel.ICommunicationObject> . Bu, tamamlanma açısından burada yer alır.  
  
 Ön koşul: yok.  
  
 Koşul sonrası: durum hata verdi. Bir özel durum oluşturabilir.  
  
 Hata () yöntemi, geçerli durum hata verdi veya kapatılırsa hiçbir şey yapmaz. Aksi takdirde, durumu hatalı olarak ayarlar ve hatalı olayı oluşturan Onkusurlu () öğesini çağırın. Onkusurlu, yeniden oluşturulduğu bir özel durum oluşturursa.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx yöntemleri  

 CommunicationObject, nesne belirli bir durumdaysa özel durum oluşturmak için kullanılabilecek üç korumalı yönteme sahiptir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> durum kapanış, kapatma veya hatalı ise bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> durum oluşturulmadıysa bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> durum açılmadıysa bir özel durum oluşturur.  
  
 Oluşturulan özel durumlar duruma bağlıdır. Aşağıdaki tabloda, bu durumu oluşturan bir ThrowIfXxx çağırarak oluşturulan farklı durumlar ve karşılık gelen özel durum türü gösterilmektedir.  
  
|Durum|Iptal çağrıldı mı?|Özel durum|  
|-----------|----------------------------|---------------|  
|Oluşturulan|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açma|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Makta|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Kapatma|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Kapatma|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Kapatıldı|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> bir nesnenin önceki ve açık bir Abort çağrısıyla kapatılmış olması durumunda. Nesne üzerinde close çağrısı yaparsanız, bir oluşturulur <xref:System.ObjectDisposedException?displayProperty=nameWithType> .|  
|Kapatıldı|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Alındı|Yok|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Zaman aşımları  

 Tartışıyoruz yöntemlerin birkaçı zaman aşımı parametrelerini alır. Bunlar kapalı, Açık (belirli aşırı yüklemeler ve zaman uyumsuz sürümler), OnClose ve OnOpen. Bu yöntemler uzun işlemlere izin vermek için tasarlanmıştır (örneğin, bir bağlantıyı düzgün bir şekilde kapatırken giriş/çıkış üzerinde engelleme), zaman aşımı parametresi, kesintiye uğramadan önce bu tür işlemlerin ne kadar sürdüğünü gösterir. Bu yöntemlerin herhangi birinin uygulamaları, bu zaman aşımı süresi içinde çağırana döndüğünden emin olmak için sağlanan zaman aşımı değerini kullanmalıdır. Zaman aşımı kullanmayan diğer yöntemlerin uygulamaları uzun işlemler için tasarlanmamıştır ve giriş/çıkış üzerinde engellenmemelidir.  
  
 Özel durum, bir zaman aşımı olmayan Open () ve Close () aşırı yüklemelerdir. Bu, türetilmiş sınıf tarafından sağlanan varsayılan bir zaman aşımı değeri kullanır. <xref:System.ServiceModel.Channels.CommunicationObject> adlı iki korumalı soyut özelliği gösterir <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> ve <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> şöyle tanımlanır:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Türetilmiş bir sınıf, bir zaman aşımı değeri kullanmayan Open () ve Close () aşırı yüklemeleri için varsayılan zaman aşımını sağlamak üzere bu özellikleri uygular. Ardından, Open () ve Close () uygulamaları varsayılan zaman aşımı değerini geçen bir zaman aşımı süresi alan aşırı yüklemeye temsilci sağlar, örneğin:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>Idefaultcommunicationzamanaşımları  

 Bu arabirimin açık, gönder, al ve Kapat için varsayılan zaman aşımı değerlerini sağlamak üzere dört salt okunurdur özelliği vardır. Her uygulama, uygun şekilde varsayılan değerleri edinmekten sorumludur. Kolaylık <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelListenerBase> sağlar ve bu değerleri 1 dakika için varsayılan olarak yapın.
