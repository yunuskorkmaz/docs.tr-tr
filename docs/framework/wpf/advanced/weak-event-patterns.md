---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 4b1e8649e5d550ffa2c7ee614cb9102f86a83ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549353"
---
# <a name="weak-event-patterns"></a>Zayıf Olay Desenleri
Uygulamalarda, olay kaynaklarına bağlı işleyicileri işleyici kaynağına eklenen dinleyici nesne birlikte yok edilmeyecek olduğunu mümkündür. Bu durum bellek sızıntıları yol açabilir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] belirli olaylar için ayrılmış yönetici sınıfı sağlayarak ve bu olay için dinleyiciler üzerinde arabirimi uygulama bu sorunu gidermek için kullanılan bir tasarım desenini tanıtır. Bu tasarım deseni olarak bilinen *zayıf olay deseni*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Neden zayıf olay deseni uygulansın mı?  
 Olayları dinleme bellek sızıntıları yol açabilir. Bir olayı dinlemek için tipik teknik kaynak üzerinde bir olay işleyici iliştirir dile özgü sözdizimi kullanmaktır. Örneğin, C# ' ta o sözdizimi şöyledir: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Bu teknik güçlü bir başvuru olay kaynağından olay dinleyicisi oluşturur. Normalde, olay işleyicisi için bir dinleyici ekleme (olay işleyicisi açıkça kaldırılmadığı sürece), kaynak nesne ömrü tarafından etkileyen bir nesne ömrü dinleyici neden olur. Ancak bazı durumlarda olup şu anda görsel ağaç uygulamanın ve kaynak ömrü tarafından ait olduğu gibi diğer faktörler tarafından denetlenmesi için dinleyici nesne ömrü isteyebilirsiniz. Kaynak nesne ömrü dinleyici nesne ömrü genişletir olduğunda, normal olay deseni bir bellek sızıntısı müşteri adayları: dinleyici istenenden daha uzun süre Canlı tutulur.  
  
 Zayıf olay deseni bu bellek sızıntısı sorununu çözmek için tasarlanmıştır. Zayıf olay düzeni için bir olay kaydetmek bir dinleyici gerekiyor, ancak ne zaman kaydı dinleyicisi açıkça bilmez olduğunda kullanılabilir. Kaynak nesne ömrü dinleyicisinin yararlı nesne ömrü aştığında zayıf olay düzeni de kullanılabilir. (Bu durumda, *yararlı* tarafından belirlenir.) Zayıf olay deseni kaydolun ve herhangi bir şekilde dinleyici nesne ömrü özelliklerini etkilemeden olay almak dinleyici sağlar. Etkin dolaylı başvuru kaynağından dinleyici atık toplama için uygun olup olmadığını belirlemez. Bu nedenle zayıf olay düzeni ve ilgili adlandırma zayıf bir başvuru başvurudur [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Dinleyici toplanan veya aksi halde yok çöp olabilir ve kaynağı artık yok nesnesine olan toplanamayan işleyici başvurularını korumadan devam edebilir.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kimin zayıf olay desenini uygular?  
 Zayıf olay düzeni uygulama öncelikle denetim yazarları için ilginç olacaktır. Denetim yazarı olarak, büyük ölçüde davranış ve kapsama denetiminizi ve takılı olduğundan uygulamaları sahip etkisi sorumludur. Bu nesne yaşam süresi davranışını denetlemeye özellikle açıklanan bellek sızıntısı sorununu işlenmesini içerir.  
  
 Belirli senaryolar kendiliğinden kendilerini zayıf olay deseni uygulamaya ödünç. Bu senaryolardan biri, veri bağlama ' dir. Veri bağlama, kaynak nesnenin bir bağlama hedefidir dinleyici nesne tamamen bağımsız olması için yaygın bir sorundur. Pek çok görünüşünün [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri zaten bağlama sahip olayları nasıl uygulandığı durumunda uygulanan zayıf olay deseni.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Zayıf olay deseni nasıl uygulanır  
 Zayıf olay desen uygulamak için üç yolu vardır. Aşağıdaki tabloda, üç yaklaşımlar listeler ve her zaman kullanmalısınız için bazı yönergeler sağlar.  
  
|Yaklaşım|Ne zaman uygulanacağını|  
|--------------|-----------------------|  
|Varolan bir zayıf olay Yöneticisi sınıfı kullanın|Abone olmak istediğiniz olayı karşılık gelen varsa <xref:System.Windows.WeakEventManager>, varolan zayıf olay Yöneticisi'ni kullanın. WPF ile birlikte zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı. Ancak, büyük olasılıkla diğer yaklaşımlardan birini seçmeniz gerekir, böylece WPF ile birlikte nispeten az zayıf olay yöneticileri olduğunu unutmayın.|  
|Bir genel zayıf olay Yöneticisi sınıf kullanma|Genel kullanmak <xref:System.Windows.WeakEventManager%602> var olan <xref:System.Windows.WeakEventManager> verimliliği hakkında kullanılabilir değil, uygulama için kolay bir yol istediğiniz ve değildir ilgilidir. Genel <xref:System.Windows.WeakEventManager%602> bir mevcut veya özel zayıf olay Yöneticisi daha az verimlidir. Örneğin, genel bir sınıf olayın adı verilen olay bulmak için daha fazla yansıma yapar. Ayrıca, olay genel kullanarak kaydetmek için kod <xref:System.Windows.WeakEventManager%602> daha ayrıntılı varolan kullanmaktan veya özel <xref:System.Windows.WeakEventManager>.|  
|Özel zayıf olay Yöneticisi sınıf oluşturma|Bir özel Oluştur <xref:System.Windows.WeakEventManager> var olan <xref:System.Windows.WeakEventManager> kullanılabilir değil ve en iyi verim istiyor. Özel bir kullanarak <xref:System.Windows.WeakEventManager> abone olmak için bir olay daha verimli olacaktır, ancak başına daha fazla kod yazmaya maliyet doğurur.|  
  
 Aşağıdaki bölümlerde zayıf olay deseni uygulayan açıklar.  Bu tartışma amaçları doğrultusunda, Abone olunacak olay aşağıdaki özelliklere sahiptir.  
  
-   Olay adı `SomeEvent`.  
  
-   Olay tarafından tetiklenir `EventSource` sınıfı.  
  
-   Olay işleyicisinin türü vardır: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).  
  
-   Olay türünü parametre olarak geçirir `SomeEventEventArgs` olay işleyicileri için.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Varolan bir zayıf olay Yöneticisi sınıfını kullanma  
  
1.  Varolan bir zayıf olay Yöneticisi bulunamıyor.  
  
     WPF ile birlikte zayıf olay yöneticileri bir listesi için bkz: devralma hiyerarşisinde <xref:System.Windows.WeakEventManager> sınıfı.  
  
2.  Normal olay bağlantı yerine yeni zayıf olay Yöneticisi'ni kullanın.  
  
     Örneğin, kodunuzu bir olaya abone olmak için aşağıdaki düzeni kullanıyorsa:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Aşağıdaki desenini değiştirin:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuzu bir olaya aboneliğinizi iptal etmek için aşağıdaki düzeni kullanıyorsa:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Aşağıdaki desenini değiştirin:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Genel zayıf olay Yöneticisi sınıfını kullanma  
  
1.  Genel kullanmak <xref:System.Windows.WeakEventManager%602> normal olay bağlantı yerine sınıfı.  
  
     Kullandığınızda <xref:System.Windows.WeakEventManager%602> olay dinleyicileri kaydetmek için olay kaynağı tedarik ve <xref:System.EventArgs> türü sınıfı ve çağrı türü parametreleri olarak <xref:System.Windows.WeakEventManager%602.AddHandler%2A> aşağıdaki kodda gösterildiği gibi:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Özel bir zayıf olay Yöneticisi sınıf oluşturma  
  
1.  Aşağıdaki sınıf şablonu projenize kopyalayın.  
  
     Bu sınıf devraldığı <xref:System.Windows.WeakEventManager> sınıfı.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  Değiştir `SomeEventWeakEventManager` kendi adıyla adı.  
  
3.  Olayınızın ilişkili adlarıyla daha önce açıklanan üç adlarını değiştirin. (`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)  
  
4.  Zayıf olay Yöneticisi sınıfı görünürlüğünü (ortak / iç / özel) aynı görünürlük yönettiği olayı olarak ayarlayın.  
  
5.  Normal olay bağlantı yerine yeni zayıf olay Yöneticisi'ni kullanın.  
  
     Örneğin, kodunuzu bir olaya abone olmak için aşağıdaki düzeni kullanıyorsa:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Aşağıdaki desenini değiştirin:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuzu bir olaya aboneliğinizi iptal etmek için aşağıdaki düzeni kullanıyorsa:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Aşağıdaki desenini değiştirin:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
