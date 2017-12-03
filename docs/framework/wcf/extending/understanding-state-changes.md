---
title: "Durum Değişikliklerini Anlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f93b1e9fdb1569507937c5381b157204ac88f87
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="understanding-state-changes"></a>Durum Değişikliklerini Anlama
Bu konuda durumları ve kanallar sahip geçişler, yapısı kanal durumları ve bunların nasıl uygulanacağını kullanılan türleri açıklanmaktadır.  
  
## <a name="state-machines-and-channels"></a>Durum makineleri ve kanallar  
 İletişim ile ilgili nesneleri örneğin yuva, genellikle, durumu geçişleri ağ kaynaklarını ayırma, yapma veya bağlantıları kapatarak ve iletişim sonlandırma kabul bağlantıları ile ilgili Durum makinesi sunar. Kanal durumu makine nesnenin temel uygulaması soyutlar iletişim nesnesi durumlardan Tekdüzen bir modeli sağlar. <xref:System.ServiceModel.ICommunicationObject> Arabirimi durumları, durum geçiş yöntemlerini ve durum geçiş olayları kümesi sağlar. Tüm kanalları, kanal fabrikaları ve kanal dinleyicileri kanal durum makinesinin uygular.  
  
 Durum geçişi gerçekleştikten sonra kapalı olarak kapatmadan önce Faulted, açık ve açma olaylarını bir dış gözlemci işaret eder.  
  
 Durdurma, kapatma ve Aç yöntemleri (ve zaman uyumsuz eşdeğerlerine) durumu geçişleri neden olur.  
  
 State özelliği tarafından tanımlandığı şekilde geçerli durumunu döndürür <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, CommunicationObject ve durumları ve durum geçişi  
 Bir <xref:System.ServiceModel.ICommunicationObject> out çeşitli özelliklerini yeri yapılandırılabilir oluşturulan durumda başlatır. Bir kez açık durumda, ileti gönderme ve alma için kullanılabilir olması ancak özelliklerini değişmez olarak kabul edilir. Kapanma durumunda nesne artık yeni gönderme işlem veya istekleri almak, ancak varolan istekleri kadar tamamlamak fırsatına sahip sonra kapatma zaman aşımını ulaşıldı.  Kurtarılamaz bir hata oluşursa, nesne nerede hata hakkında bilgi için Denetlenmekte ve olması sonuçta kapalı Faulted bir duruma geçer. Kapalı durumunda nesne temelde durum makinesinin sonuna ulaştı olduğunda. Bir kez bir nesne geçişleri bir durumdan diğerine onu geri önceki bir duruma geçmez.  
  
 Aşağıdaki diyagramda gösterildiği <xref:System.ServiceModel.ICommunicationObject> durumları ve durum geçişlerinin. Durumu geçişleri üç yöntemi çağrılarak kaynaklanabilir:, açık, iptal etmek veya kapatın. Bunlar, diğer uygulamaya özel yöntemler çağrılarak da kaynaklanabilir. Faulted durumuna geçiş hataları açma sırasında veya iletişim nesnesi açılan sonra sonucu olarak meydana gelmiş olabilir.  
  
 Her <xref:System.ServiceModel.ICommunicationObject> oluşturulan durumdaki out başlatır. Bu durumda, nesne özelliklerini ayarlayarak uygulamanın yapılandırabilirsiniz. Bir nesne oluşturulan dışında bir duruma geldiğinde, sabit olarak değerlendirilir.  
  
 ![Kanal durumu transitition](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Şekil 1 '. ICommunicationObject durum makinesinin.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]adlı bir Özet temel sınıf sağlar <xref:System.ServiceModel.Channels.CommunicationObject> uygulayan <xref:System.ServiceModel.ICommunicationObject> ve kanal durum makinesinin. Aşağıdaki grafikte özgü bir değiştirilmiş durumu diyagramıdır <xref:System.ServiceModel.Channels.CommunicationObject>. Ek olarak <xref:System.ServiceModel.ICommunicationObject> Durum makinesi ek zaman zamanlama gösterir <xref:System.ServiceModel.Channels.CommunicationObject> yöntemleri çağrılır.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Şekil 2 '. Olayları ve korumalı yöntemler çağrıları dahil olmak üzere ICommunicationObject durum makinesinin CommunicationObject uygulanması.  
  
### <a name="icommunicationobject-events"></a>ICommunicationObject olayları  
 <xref:System.ServiceModel.Channels.CommunicationObject>tarafından tanımlanan beş olayları gösterir <xref:System.ServiceModel.ICommunicationObject>. Bu olaylar durumu geçişleri bildirim almak için iletişim nesnesi kullanarak kod için tasarlanmıştır. Nesnenin durumu olayı tarafından adlı durumu geçişleri sonra yukarıdaki Şekil 2'de gösterildiği gibi her olay bir kez tetiklenir. Tüm beş olayları çeken `EventHandler` olarak tanımlanan türü:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 İçinde <xref:System.ServiceModel.Channels.CommunicationObject> , gönderenin uygulamasıdır ya da <xref:System.ServiceModel.Channels.CommunicationObject> kendisini veya ne olursa olsun gönderene olarak geçirildi <xref:System.ServiceModel.Channels.CommunicationObject> (Bu Oluşturucusu aşırı kullanılıyorsa) Oluşturucusu. EventArgs parametresi `e`, her zaman `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Türetilen nesne geri aramalar  
 Beş olayları yanı sıra <xref:System.ServiceModel.Channels.CommunicationObject> sekiz korumalı sanal yöntemler önce ve durumu geçişleri oluştuktan sonra geri çağrılması için türetilmiş bir nesne izin verecek şekilde tasarlanmıştır bildirir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> Ve <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> yöntemleri her biriyle ilişkili üç tür geri aramalar sahip. Örneğin, karşılık gelen <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> var. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. İle ilişkili <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> olan <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> yöntemleri.  
  
 Benzer şekilde, <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> yöntemi sahip karşılık gelen <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Sırada <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> varsayılan uygulaması varsa, diğer geri çağırmaları durumu makine doğruluk için gerekli olan varsayılan uygulama vardır. Bu yöntemi geçersiz kılarsanız temel uygulamayı çağırması veya doğru şekilde değiştirmek emin olun.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> ilgili harekete <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> olaylar. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>ve <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nesne durumu açık ve kapalı sırasıyla ayarlayın, sonra da ilgili harekete <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> olaylar.  
  
### <a name="state-transition-methods"></a>Durum geçişi yöntemleri  
 <xref:System.ServiceModel.Channels.CommunicationObject>Durdurma, kapatma ve açık uygulamaları sağlar. Ayrıca, bir durum geçişi Faulted duruma neden olan bir arıza yöntemi sağlar. Şekil 2 gösterir <xref:System.ServiceModel.ICommunicationObject> (son etiketli geçiş neden yöntemin kullanımı içinde durum etiketlenmemiş geçişleri) neden yöntemi tarafından etiketli her geçiş durumu makineyle.  
  
> [!NOTE]
>  Tüm <xref:System.ServiceModel.Channels.CommunicationObject> iletişimin uygulamaları durum alır/ayarlar iş parçacığı eşitlenir.  
  
 Oluşturucu  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>üç sağlar Oluşturucular, oluşturulan durumunda her biri bırakın nesne. Oluşturucular olarak tanımlanır:  
  
 İlk Oluşturucusu nesneyi alır Oluşturucusu aşırı temsilciler varsayılan bir oluşturucu şöyledir:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Bir nesne alan oluşturucu iletişim nesne durumu erişimi eşitlerken kilitlenmesine nesnesi olarak bu parametrenin kullanır:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Son olarak, üçüncü bir oluşturucu gönderen bağımsız değişken olarak kullanılan ek bir parametre alır, <xref:System.ServiceModel.ICommunicationObject> olaylar.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Önceki iki oluşturucular gönderen için bunu ayarlayın.  
  
 Open yöntemi  
  
 Önkoşul: Durum oluşturulur.  
  
 Sonrası koşul: Açık veya Faulted durumudur. Bir özel durum.  
  
 Open() yöntemi iletişim nesnesi açın ve durumunu ayarlamak için açık dener. Bir hatayla karşılaştığında, durumu için Faulted ayarlarsınız.  
  
 Yöntemi, geçerli durumu oluşturduğunuz ilk denetler. Geçerli durumu açma veya atar açılmış bir <xref:System.InvalidOperationException>. Geçerli durumu kapatma ya da kapalı olduğunda oluşturur bir <xref:System.ServiceModel.CommunicationObjectAbortedException> nesne sona erdiğinde ve <xref:System.ObjectDisposedException> Aksi takdirde. Geçerli durumu hatalı olursa oluşturur bir <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Ardından durumu için açılış ayarlar ve bu sırayla (hangi açma olayını) OnOpening(), OnOpen() ve OnOpened() çağırır. OnOpened() durumu açık için ayarlar ve açılan olayını başlatır. Bu atar varsa bir özel durum, açık () Fault() çağıran ve özel durum Kabarcık olanak tanır. Aşağıdaki diyagramda açık işlem daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Bir iç iletişim nesnesi açma gibi özel açık mantığını uygulamak için açıldığında yöntemini geçersiz kılın.  
  
 Close Yöntemi  
  
 Önkoşul: yok.  
  
 Sonrası koşul: Durumu kapalı. Bir özel durum.  
  
 Herhangi bir durum çağrısının yöntemi çağrılabilir. Nesne normal olarak kapatmak çalışır. Bir hatayla karşılaştı nesne sonlandırır. Yöntemi, hiçbir şey geçerli durumunda kapatma veya kapalı yapar. Aksi takdirde, durumu kapatma ayarlar. Özgün durumuna oluşturma, açma veya Faulted idiyse, Abort() çağırır (Aşağıdaki diyagramda bakın). Özgün durumuna açılmışsa, o sırada (hangi kapanış olayını) OnClosing(), OnClose() ve OnClosed() çağırır. Bu atar varsa bir özel durum, Kapat () Abort() çağıran ve özel durum Kabarcık olanak tanır. OnClosed() durumunu Kapalı olarak ayarlar ve kapalı olayını başlatır. Aşağıdaki diyagram kapatma işlem daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Bir iç iletişim nesnesi kapatma gibi özel Kapat mantığını uygulamak için OnClose yöntemi geçersiz kılın. Tüm normal bir zaman aşımı parametresi aldığından (örneğin, diğer taraftaki yanıt vermesi bekleniyor) uzun bir süre içinde OnClose() uygulanması gerekir ve Abort() bir parçası olarak çağrılmaz çünkü engelleyebilir mantığı kapatma.  
  
 Durdurma  
  
 Önkoşul: yok.  
Sonrası koşul: Durumu kapalı. Bir özel durum.  
  
 Geçerli durumu kapalı veya nesne önce (örneğin, büyük olasılıkla başka bir iş parçacığında Abort() yürütülmekte olan tarafından) sonlanıp sonlanmadığını ise Abort() yöntemi hiçbir şey yapmaz. Aksi halde Durum Kapanış için ayarlar ve (hangi kapanış olayını) OnClosing(), OnAbort() ve OnClosed() (nesne sonlandırıldı çünkü OnClose kapalı çağırmaz) bu sırayla çağırır. OnClosed() durumunu Kapalı olarak ayarlar ve kapalı olayını başlatır. Bunlardan herhangi bir özel durum, iptal çağırana yeniden oluşturulur. Uygulamaları OnClosing(), OnClosed() ve OnAbort() (örneğin, giriş/çıkış üzerinde) bloğu değil. Aşağıdaki diyagramda durdurma işlemi daha ayrıntılı olarak gösterilmiştir.  
  
 ![Durum değişiklikleri](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Geçersiz kılma OnAbort yöntemini özel uygulamak üzere bir iç iletişim nesnesi sonlandırma gibi mantığı sonlanır.  
  
 Hata  
  
 Hataya yöntemi özgüdür <xref:System.ServiceModel.Channels.CommunicationObject> ve parçası <xref:System.ServiceModel.ICommunicationObject> arabirimi. Onu buraya bütünlük açısından dahil edilmiştir.  
  
 Önkoşul: yok.  
  
 Sonrası koşul: Durumu hatalı. Bir özel durum.  
  
 Geçerli durumu Faulted ya da kapalı olduğunda Fault() yöntemi hiçbir şey yapmaz. Aksi takdirde Faulted ve çağrı Faulted olayını OnFaulted() durumunu ayarlar. OnFaulted bir özel durum oluşturursa yeniden oluşturulur.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx yöntemleri  
 CommunicationObject nesne belirli bir durumda ise özel durumlar oluşturma için kullanılan üç korumalı yöntemlerine sahiptir.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>Durum kapanış, kapalı veya Faulted ise özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>durumu olmayan oluşturulursa, bir özel durum oluşturur.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>durumu olmayan açılırsa bir özel durum oluşturur.  
  
 Oluşturulan özel durumları durumuna bağlıdır. Aşağıdaki tabloda farklı durumları ve bu durumda oluşturur ThrowIfXxx çağrılarak oluşturulan karşılık gelen özel durum türünü gösterir.  
  
|Durum|Abort çağrılmış var?|Özel Durum|  
|-----------|----------------------------|---------------|  
|Oluşturuldu|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açma|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Açılan|Yok|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Kapatma|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|Kapatma|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Closed|Evet|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>bir nesne bir iptal önceki ve açık çağrısı tarafından kapatıldı durumda. Bir nesne üzerinde Kapat çağırırsanız sonra bir <xref:System.ObjectDisposedException?displayProperty=nameWithType> oluşturulur.|  
|Closed|Hayır|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Hatalı|Yok|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Zaman aşımları  
 Biz bahsedilen yöntemler çeşitli zaman aşımı parametre alır. Bunlar, Kapat, açık (belirli aşırı yüklemeleri ve zaman uyumsuz sürümlere), OnClose ve açıldığında olan. Bu yöntemleri, uzun işlemleri (örneğin, düzgün biçimde bağlantı kapatma sırasında giriş/çıkış engelleme) izin verecek şekilde tasarlanmıştır zaman aşımı parametresi ne kadar süreyle gösterir şekilde gibi işlemleri kesintiye önce alabilir. Bu yöntemlerin herhangi biriyle uygulamaları sağlanan zaman aşımı değeri bu zaman aşımı süresi içinde çağırana döndürür sağlamak için kullanmalısınız. Zaman aşımı almayan diğer yöntemleri, uygulamalarını uzun işlemleri için tasarlanmamıştır ve giriş/çıkış üzerinde Engellemiyor tamamı.  
  
 Özel bir zaman aşımı almayan Open() ve çağrısının aşırı durumdur. Bu türetilmiş sınıf tarafından sağlanan varsayılan zaman aşımı değerini kullanın. <xref:System.ServiceModel.Channels.CommunicationObject>çıkarır, iki korumalı adlı soyut özellikleri <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> ve <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> olarak tanımlanır:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Türetilmiş bir sınıf bir zaman aşımı değeri almayan Open() ve çağrısının aşırı için varsayılan zaman aşımı sağlamak için bu özellikleri uygular. Ardından Open() ve çağrısının uygulamaları için varsayılan zaman aşımı değeri, örneğin geçirme zaman aşımını alır aşırı temsilci:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Bu arabirim açmak, gönderme, alma ve kapatmak varsayılan zaman aşımı değerlerini sağlamak için dört salt okunur özellikler vardır. Her uygulama, uygun herhangi bir şekilde varsayılan değerleri almak için sorumludur. Kolaylık, <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase> varsayılan bu değerleri 1 dakika.
