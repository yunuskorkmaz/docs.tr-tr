---
title: Durum Değişikliklerini Anlama
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 5bfee392053d9f3fd529d68b533a046e53f20dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771620"
---
# <a name="understanding-state-changes"></a>Durum Değişikliklerini Anlama
Bu konuda, durumları ve kanalları sahip geçişleri, yapı kanal durumları ve bunların nasıl uygulanacağını kullanılan türleri açıklanmaktadır.  
  
## <a name="state-machines-and-channels"></a>Durum makineleri ve kanallar  
 İletişim ile ilgili nesneleri örneğin yuva, genellikle ağ kaynaklarını ayırma, yapmadan veya bağlantıları kapatarak ve iletişim sonlandırma kabul bağlantıları olan durumu geçişleri ilgili bir Durum makinesi sunar. Kanal durumu makine, o nesnenin temel uygulamayı soyutlayan bir iletişim nesnesi durumlarının Tekdüzen bir modeli sağlar. <xref:System.ServiceModel.ICommunicationObject> Arabirimi durumları, durum geçiş yöntemlerini ve durum geçiş olayları kümesi sağlar. Kanal durumu makine, tüm kanallar, kanal fabrikaları ve kanal dinleyicileri uygulayın.  
  
 Bir durum geçişi tamamlandıktan sonra kapalı olarak kapatmadan önce hatalı, açık ve açılış olaylarını bir dış gözlemci sinyal.  
  
 Durum geçişlerini durdurma, kapatma ve açık yöntemleri (ve zaman uyumsuz eşdeğerlerine) neden.  
  
 State özelliği tarafından tanımlanan geçerli durumunu döndürür <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, CommunicationObject ve durumları ve durum geçişi  
 Bir <xref:System.ServiceModel.ICommunicationObject> out burada çeşitli özellikleri yapılandırılabilir Created durumunda başlar. Bir kez Opened durumunda ileti gönderme ve alma için kullanışlı bir nesnedir ancak özelliklerini sabit olarak kabul edilir. Kapatma durumunda, nesne artık yeni gönderme işlemi veya isteklerini almak, ancak mevcut isteklerini kadar tamamlanması şansına sahip sonra Close zaman aşımı ulaşıldı.  Kurtarılamaz bir hata oluşursa, nesne Burada, kullanılabilir hata hakkında daha fazla bilgi için inceledi ve sonuçta kapalı hatalı durumuna geçer. Zaman kapalı durumda nesne aslında durum makinesinin sonuna ulaştı. Bir kez bir nesne geçişleri bir durumdan diğerine, geri önceki bir duruma geçmez.  
  
 Aşağıdaki diyagramda gösterildiği <xref:System.ServiceModel.ICommunicationObject> durumları ve durum geçişlerini. Durum geçişlerini üç yöntemden birini çağırarak neden olabilir. , Açık, durdurmak veya kapatın. Bunlar, diğer uygulamaya özel yöntemleri çağırarak da kaynaklanabilir. Hatalı durumuna geçiş hataları açma sırasında veya sonrasında iletişim nesnesi açık nedeniyle meydana gelmiş olabilir.  
  
 Her <xref:System.ServiceModel.ICommunicationObject> Created durumundaki out başlatır. Bu durumda, uygulamanın nesne özelliklerini ayarlayarak yapılandırabilirsiniz. Dışında oluşturulan bir durumda bir nesne eklendiğinde, sabit olarak değerlendirilir.  
  
 ![Kanal durumu transitition](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Şekil 1. ICommunicationObject Durum makinesi.  
  
 Windows Communication Foundation (WCF) adlı bir soyut temel sınıf sağlar <xref:System.ServiceModel.Channels.CommunicationObject> uygulayan <xref:System.ServiceModel.ICommunicationObject> ve kanal Durum makinesi. Aşağıdaki grafikte özgü bir değiştirilme diyagramıdır <xref:System.ServiceModel.Channels.CommunicationObject>. Ek olarak <xref:System.ServiceModel.ICommunicationObject> Durum makinesi ek zaman zamanlamasını gösterir <xref:System.ServiceModel.Channels.CommunicationObject> yöntemi çağrılır.  
  
 ![Durumu değiştiğinde](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Şekil 2. Olayları ve korumalı yöntemlere çağrılar dahil olmak üzere ICommunicationObject durum makinesinin CommunicationObject uygulaması.  
  
### <a name="icommunicationobject-events"></a>ICommunicationObject olayları  
 <xref:System.ServiceModel.Channels.CommunicationObject> tarafından tanımlanan beş olayları ortaya koyan <xref:System.ServiceModel.ICommunicationObject>. Bu olaylar, durum geçişlerini bildirilmesi için iletişim nesnesi kullanarak kod için tasarlanmıştır. Adlı olayın durumu için nesnenin durumu geçişleri sonra yukarıdaki Şekil 2'de gösterildiği gibi her olay bir kez tetiklenir. Tüm beş olayları çeken `EventHandler` olarak tanımlanan bir türü:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 İçinde <xref:System.ServiceModel.Channels.CommunicationObject> , gönderen uygulamasıdır ya da <xref:System.ServiceModel.Channels.CommunicationObject> kendisini veya ne olursa olsun gönderene olarak geçirilen <xref:System.ServiceModel.Channels.CommunicationObject> Oluşturucusu (oluşturucu aşırı yükleyen kullanılıyorsa). EventArgs parametresi `e`, her zaman `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Türetilmiş nesneden geri çağırmaları  
 Beş olayları yanı sıra <xref:System.ServiceModel.Channels.CommunicationObject> sekiz korumalı sanal yöntemler önce ve sonra durumu geçişleri ortaya Aranmak üzere bir türetilmiş nesne izin vermek için tasarlanmış bildirir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> Ve <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> yöntemler her biriyle ilişkili üç tür geri çağırmaları sahiptir. Örneğin, karşılık gelen <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> yoktur <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. İle ilişkili <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> olan <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> yöntemleri.  
  
 Benzer şekilde, <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> yöntemi olan bir karşılık gelen <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Sırada <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> varsayılan uygulaması varsa, durum makine doğruluk için gerekli olan varsayılan bir uygulama, diğer geri çağırmaları sahip değilsiniz. Bu yöntemi geçersiz kılarsanız, temel uygulamayı çağırması veya doğru şekilde değiştirmek emin olun.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> ilgili harekete <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> olayları. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> açık ve kapalı nesne durumu sırasıyla ayarlayın, sonra ilgili harekete <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> olayları.  
  
### <a name="state-transition-methods"></a>Durum geçişi yöntemleri  
 <xref:System.ServiceModel.Channels.CommunicationObject> Durdurma, kapatma ve açma uygulamalarını sağlar. Ayrıca, bir durum geçişi hatalı durumuna neden olan hata yöntemi sağlar. Şekil 2 gösterir <xref:System.ServiceModel.ICommunicationObject> (etiketlenmemiş geçişleri son etiketli geçiş yaptığını yöntemin uygulanmasını içinde sorun) neden yöntemi tarafından etiketlenmiş her geçiş ile Durum makinesi.  
  
> [!NOTE]
>  Tüm <xref:System.ServiceModel.Channels.CommunicationObject> uygulamaları iletişim durumunu alır/ayarlar iş parçacığı eşitlenir.  
  
 Oluşturucu  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> üç sağlar Oluşturucular, Created durumunda her biri bırakın nesne. Oluşturucular olarak tanımlanır:  
  
 İlk Oluşturucu, nesneyi alan oluşturucu aşırı yüklemesini için temsilciler varsayılan bir oluşturucu şöyledir:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Bir nesne alan oluşturucu iletişim nesne durumu erişimi eşitlerken kilitlenmesine nesnesi olarak bu parametre kullanır:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Son olarak, üçüncü Oluşturucu gönderen bağımsız değişken olarak kullanılan ek bir parametre alır, <xref:System.ServiceModel.ICommunicationObject> olaylar.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Önceki iki Oluşturucu gönderen için bunu ayarlayın.  
  
 open yöntemi  
  
 Önkoşul: Durum oluşturulur.  
  
 Sonrası koşul: Açık veya hatalı durumudur. Bir özel durum oluşturabilir.  
  
 Open() yöntemi iletişim nesnesi açın ve durumunu ayarlamak için açık dener. Bu hatayla karşılaşılırsa, için hatalı durumuna ayarlanır.  
  
 Yöntemin ilk geçerli durumu oluşturduğunuz denetler. Geçerli durumu açılış veya atar açılan bir <xref:System.InvalidOperationException>. Geçerli durumu, kapatma veya kapalı ise, onu oluşturur bir <xref:System.ServiceModel.CommunicationObjectAbortedException> nesne sonlandırıldıysa ve <xref:System.ObjectDisposedException> Aksi takdirde. Geçerli durumu hatalı olursa oluşturur bir <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Açılış durumuna ayarlar ve bu sırada (Bu açılış olayını) OnOpening() ve OnOpen() OnOpened() çağırır. OnOpened() durumu için açılan ayarlar ve açılan olayını başlatır. Bu oluşturur biri geçerliyse bir özel durum, açık () Fault() çağırır ve özel durum Kabarcık olanak tanır. Aşağıdaki diyagramda açma işlemi daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durumu değiştiğinde](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Bir iç iletişim nesnesi açma gibi açık özel mantığı uygulamak için açıldığında yöntemi yok sayın.  
  
 Close Yöntemi  
  
 Önkoşul: Yok.  
  
 Sonrası koşul: Durumu kapalı. Bir özel durum oluşturabilir.  
  
 Herhangi bir durumu Close() yöntemi çağrılabilir. Nesne normal olarak kapatmak çalışır. Bir hatayla karşılaştı, nesne sonlandırır. Yöntemi, hiçbir şey geçerli durumu kapatılıyorsa veya kapalı yapar. Aksi takdirde, durumu kapatma ayarlar. Özgün durumuna oluşturma, açma ya da hatalı ise, Abort() çağırır (aşağıdaki diyagrama bakın). Özgün durum açılmışsa, o sırada (Bu kapatma olayı oluşturursa) OnClosing() ve OnClose() OnClosed() çağırır. Herhangi biri bu oluşturur bir özel durum, Kapat () Abort() çağıran ve özel durum Kabarcık sağlar. OnClosed() durumunu Kapalı olarak ayarlar ve kapalı olay başlatır. Aşağıdaki diyagram, kapatma işlemi ayrıntılı olarak gösterir.  
  
 ![Durumu değiştiğinde](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Bir iç iletişim nesnesi kapatma gibi özel Kapat mantığını uygulamak için OnClose yöntemi yok sayın. Tüm normal (örneğin, diğer taraftan yanıt vermesi bekleniyor) uzun bir zaman aşımı parametresi alan çünkü OnClose() içinde uygulanması gereken ve Abort() bir parçası olarak çağrılmaz çünkü engelleyebilir mantıksal kapatma.  
  
 Durdurma  
  
 Önkoşul: Yok.  
Sonrası koşul: Durumu kapalı. Bir özel durum oluşturabilir.  
  
 Geçerli durumu kapalı veya nesne önce (örneğin, büyük olasılıkla Abort() üzerinde başka bir iş parçacığının sahip olarak) sonlanıp sonlanmadığını ise Abort() yöntemi hiçbir şey yapmaz. Aksi halde Kapanış için ayarlar ve (hangi kapatma olayı oluşturursa) OnClosing() OnAbort() ve OnClosed() (nesne sonlandırılıyor çünkü OnClose kapalı çağırmaz) bu sırayla çağırır. OnClosed() durumunu Kapalı olarak ayarlar ve kapalı olay başlatır. Herhangi bir özel durum, iptal çağırana yeniden oluşturulmuş olur. OnClosing(), OnClosed() ve OnAbort() uygulamaları (örneğin, giriş/çıkış üzerinde) engellemediğinizden. Aşağıdaki diyagramda durdurma işlemi daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durumu değiştiğinde](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Geçersiz kılma özel uygulamak için OnAbort yöntemi gibi bir iç iletişim nesnesi sonlandırma mantığını sonlandırın.  
  
 Hata  
  
 Hata yöntemi özeldir <xref:System.ServiceModel.Channels.CommunicationObject> ve parçası <xref:System.ServiceModel.ICommunicationObject> arabirimi. Burada bütünlük açısından dahil edilmiştir.  
  
 Önkoşul: Yok.  
  
 Sonrası koşul: Durum hatalı. Bir özel durum oluşturabilir.  
  
 Geçerli durumu hatalı veya kapalı ise Fault() yöntemi hiçbir şey yapmaz. Aksi takdirde hatalı ve çağrı, hatalı olayını OnFaulted() durumunu ayarlar. OnFaulted bir özel durum oluşturursa yeniden oluşturulur.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx yöntemleri  
 CommunicationObject nesne belirli bir durumda ise özel durumlar için kullanılabilecek üç korumalı yöntemler vardır.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> durumu kapatma, kapalı veya hatalı ise bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> durumu olmayan oluşturduysanız bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> Durum açık değil bir özel durum oluşturur.  
  
 Oluşturulan özel durumlar, durumuna bağlıdır. Aşağıdaki tabloda, farklı durumları ve bu durumu oluşturan bir ThrowIfXxx çağrılarak oluşturulan karşılık gelen özel durum türünü gösterir.  
  
|Durum|Abort çağrıldıktan?|Özel Durum|  
|-----------|----------------------------|---------------|  
|Oluşturuldu|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açma|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açılan|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Kapatma|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Kapatma|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Closed|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> bir nesne bir iptal önceki ve açık çağrısı tarafından kesildi durumda. Kapanış nesnesinde çağırırsanız bir <xref:System.ObjectDisposedException?displayProperty=nameWithType> oluşturulur.|  
|Closed|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Hatalı|Yok|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Zaman Aşımları  
 Çeşitli yöntemleri ele aldığımız zaman aşımı parametre alır. Kapat ve açık (bazı aşırı yüklemeler ve zaman uyumsuz sürümleri), OnClose ve açıldığında bunlar. Bu yöntemler (örneğin, bir bağlantı düzgün biçimde kapatma sırasında giriş/çıkış üzerinde engelleme) uzun işlemler için izin vermek için tasarlanmış ne kadar zaman aşımı parametresi gösterir şekilde bu işlemleri kesintiye önce alabilir. Bu yöntemlerin herhangi biriyle uygulamaları sağlanan zaman aşımı değeri bu zaman aşımı süresi içinde çağırana döner emin olmak için kullanmanız gerekir. Bir zaman aşımı almayan diğer yöntemleri uygulamaları uzun işlemler için tasarlanmamıştır ve giriş/çıkış hakkında engelleyin değil.  
  
 Özel bir zaman aşımı almayan Open() ve Close() aşırı durumdur. Bu, türetilmiş sınıf tarafından sağlanan varsayılan zaman aşımı değerini kullanın. <xref:System.ServiceModel.Channels.CommunicationObject> kullanıma sunan, iki korumalı adlı soyut Özellikler <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> ve <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> olarak tanımlanır:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Türetilmiş bir sınıf, bir zaman aşımı değeri almayan Open() ve Close() aşırı için varsayılan zaman aşımı sağlamak için bu özellikleri uygular. Ardından Open() ve Close() uygulamaları varsayılan zaman aşımı değeri, örneğin geçirerek bir zaman aşımı alan aşırı yüklemesini için temsilci seçme:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Bu arabirim açın, gönderme, alma ve kapatmak varsayılan zaman aşımı değerlerini sağlamak için dört salt okunur özelliklere sahiptir. Her uygulama, varsayılan değerleri uygun herhangi bir şekilde almak için sorumludur. Bir kolaylık olarak <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase> varsayılan bu değerler her biri 1 dakika.
