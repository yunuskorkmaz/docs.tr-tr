---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: e0cd6837de626fa6bcd560811c6a70f7f6604daa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316173"
---
# <a name="weak-event-patterns"></a>Zayıf Olay Desenleri
Uygulamalar, olay kaynaklarına bağlı işleyicileri işleyicinin kaynağına bağlı dinleyici nesne ile koordinasyon halinde edilmeyeceği olduğunu mümkündür. Bu durum, bellek sızıntılarının neden olabilir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] belirli olaylar için adanmış yönetici sınıfı sağlayarak ve bu olayın dinleyicileri üzerinde arabirimi uygulama bu sorunu gidermek için kullanılabilecek bir tasarım desenini tanıtır. Bu tasarım deseni olarak bilinen *zayıf olay deseni*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Zayıf olay deseni neden uygulansın mı?  
 Olayları dinleme bellek sızıntılarının neden olabilir. Bir olayı dinlemek için genel teknik, bir kaynak bir olaya bir işleyici ekler dile özgü sözdizimi kullanmaktır. Örneğin, C#, sözdizimi şöyledir: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Bu teknik, olay kaynağından olay dinleyicisi için güçlü bir başvuru oluşturur. Normalde, bir dinleyici için bir olay işleyici ekleme (olay işleyici açıkça kaldırılana sürece), kaynak nesnenin ömrünü tarafından etkileyen bir nesne yaşam süresi dinleyici neden olur. Ancak bazı durumlarda, şu anda uygulama ve kaynak ömrünü tarafından görsel ağacı ait olup gibi diğer faktörler tarafından denetlenmesi için dinleyici nesne ömrünü isteyebilirsiniz. Kaynak nesne ömrü dinleyici nesne yaşam süresi genişletir olduğunda, normal olay deseni bir bellek sızıntısına neden olur: dinleyici istenenden daha uzun süre tutma tutulur.  
  
 Zayıf olay deseni, bu bellek sızıntısı sorunu çözmek için tasarlanmıştır. Zayıf olay deseni bir etkinliğe kaydolmak bir dinleyici gerekiyor, ancak zaman kaydını kaldırmak dinleyici açıkça bilmez olduğunda kullanılabilir. Zayıf olay deseni, kaynak nesnenin ömrünü dinleyicisinin yararlı nesne yaşam süresi değerini aştığında de kullanılabilir. (Bu durumda, *yararlı* sizin tarafından belirlenir.) Zayıf olay deseni için kaydolun ve nesne yaşam süresi özellikleri herhangi bir şekilde dinleyicinin etkilemeden olay almak dinleyici sağlar. Aslında, kaynak dolaylı başvuru dinleyici çöp toplama işlemi için uygun olup olmadığını belirlemez. Bu nedenle zayıf olay deseni ve ilgili adlandırma zayıf bir başvuru başvurudur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Dinleyici atık toplanan veya yok olabilir ve kaynak toplanamayan işleyici başvuruları artık yok edilmiş nesne korumadan devam edebilirsiniz.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Zayıf olay deseni uygular kim?  
 Zayıf olay deseni uygulama öncelikli olarak denetim yazarları için ilginç. Bir denetim yazarı olarak kapsama, Denetim ve takılı olduğundan uygulamaları olan etkisini ve davranışı için büyük ölçüde sorumlu olursunuz. Bu denetim nesne yaşam süresi davranışı, özellikle açıklandığı gibi bir bellek sızıntısı sorununu işlenmesini içerir.  
  
 Belirli senaryolar kendiliğinden kendilerini zayıf olay deseni uygulamayı kiralamak. Veri bağlama, böyle bir senaryodur. Veri bağlamasında, bağlama hedefi olan dinleyici nesnesinin tamamen bağımsız olarak kaynak nesnesi yaygındır. Birçok yönden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama zaten sahip olayları nasıl uygulandığını içinde uygulanan zayıf olay deseni.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Zayıf olay deseni uygulama  
 Zayıf olay deseni uygulamak için üç yolu vardır. Aşağıdaki tabloda, üç yaklaşımları listeler ve ne zaman kullanmanız gerektiği için bazı yönergeler sağlar.  
  
|Yaklaşım|Ne zaman uygulanacağını|  
|--------------|-----------------------|  
|Varolan bir zayıf olay manager sınıfı kullanın|Abone olmak istediğiniz olayı karşılık gelen varsa <xref:System.Windows.WeakEventManager>, mevcut zayıf olay Yöneticisi'ni kullanın. WPF ile birlikte gelen zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı. Dahil edilen zayıf olay yöneticileri sınırlı olduğundan, diğer yaklaşımlar birini gerekecektir.|  
|Bir genel zayıf olay manager sınıf kullanma|Genel bir <xref:System.Windows.WeakEventManager%602> var <xref:System.Windows.WeakEventManager> kullanılabilir değilse, istediğiniz uygulama için kolay bir yol ve değilseniz verimliliği hakkında endişe duymaktadır. Genel <xref:System.Windows.WeakEventManager%602> bir mevcut veya özel zayıf olay Yöneticisi az verimlidir. Örneğin, genel bir sınıf olayın adı verilen olay bulmak için daha fazla yansıma yapar. Ayrıca, olay genel kullanarak kaydetmek için kod <xref:System.Windows.WeakEventManager%602> daha var olan bir daha ayrıntılı veya özel <xref:System.Windows.WeakEventManager>.|  
|Özel bir zayıf olay manager sınıfı oluşturma|Bir özel Oluştur <xref:System.Windows.WeakEventManager> var <xref:System.Windows.WeakEventManager> kullanılabilir değil ve en iyi verim istiyor. Özel bir kullanarak <xref:System.Windows.WeakEventManager> abone olmak için bir olay daha verimli olacaktır, ancak başına daha fazla kod yazmayı ücret.|  
|Bir üçüncü taraf zayıf olay Yöneticisi'ni kullanın|NuGet sahip [birkaç zayıf olay yöneticileri](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) ve birçok WPF çerçeveleri düzeni de destekler (örneği için bkz: [gevşek olay aboneliği Prism'ın belgelerine](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).|

 Zayıf olay deseni uygulamak nasıl aşağıdaki bölümlerde açıklanmaktadır.  Bu tartışma amacı doğrultusunda, olay abone olmak için aşağıdaki özelliklere sahiptir.  
  
-   Olay adı `SomeEvent`.  
  
-   Olay tarafından gerçekleştirilen `EventSource` sınıfı.  
  
-   Olay işleyicisinin türü vardır: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).  
  
-   Olay türünde bir parametre geçirir `SomeEventEventArgs` olay işleyicilerine.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Mevcut bir zayıf olay Manager sınıfını kullanma  
  
1. Mevcut bir zayıf olay Yöneticisi bulunamıyor.  
  
     WPF ile birlikte gelen zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.  
  
2. Normal olay birleştirme yerine yeni zayıf olay Yöneticisi'ni kullanın.  
  
     Örneğin, kodunuz bir olaya abone olmak için şu desene kullanıyorsa:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Bu da aşağıdaki deseni için değiştirin:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuzu bir olayın aboneliğini kaldırmak için şu desene kullanıyorsa:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Bu da aşağıdaki deseni için değiştirin:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Genel zayıf olay Manager sınıfını kullanma  
  
1. Genel <xref:System.Windows.WeakEventManager%602> sınıfı yerine normal olay birleştirme.  
  
     Kullanırken <xref:System.Windows.WeakEventManager%602> olay dinleyicileri kaydetmek için olay kaynağı sağlamanız ve <xref:System.EventArgs> türü olarak sınıfı ve çağrı için tür parametreleri <xref:System.Windows.WeakEventManager%602.AddHandler%2A> aşağıdaki kodda gösterildiği gibi:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Özel bir zayıf olay Yöneticisi sınıfı oluşturma  
  
1. Aşağıdaki sınıf şablonu projenize kopyalayın.  
  
     Bu sınıf devraldığı <xref:System.Windows.WeakEventManager> sınıfı.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Değiştirin `SomeEventWeakEventManager` kendi adıyla adı.  
  
3. Etkinliğiniz için karşılık gelen adları ile daha önce açıklanan üç adlarını değiştirin. (`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)  
  
4. Zayıf olay manager sınıfı görünürlüğünü (Genel / iç / özel) aynı görünürlük yönettiği olayı olarak ayarlayın.  
  
5. Normal olay birleştirme yerine yeni zayıf olay Yöneticisi'ni kullanın.  
  
     Örneğin, kodunuz bir olaya abone olmak için şu desene kullanıyorsa:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Bu da aşağıdaki deseni için değiştirin:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuz için bir olay aboneliği için şu desene kullanıyorsa:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Bu da aşağıdaki deseni için değiştirin:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
