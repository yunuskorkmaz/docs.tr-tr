---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: c0bf92c9b6046d531e75771a9205e6dffe0fd367
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458489"
---
# <a name="weak-event-patterns"></a>Zayıf Olay Desenleri
Uygulamalarda, olay kaynaklarına eklenmiş olan işleyiciler, işleyiciyi kaynağa bağlayan dinleyici nesnesiyle birlikte yok edilmez. Bu durum bellek sızıntılarına neden olabilir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], belirli olaylar için adanmış bir yönetici sınıfı sağlayarak ve bu olay için dinleyicilerine bir arabirim uygulayarak bu sorunu gidermek için kullanılabilecek bir tasarım deseninin ortaya koymaktadır. Bu tasarım deseninin *zayıf olay deseninin*olduğu bilinmektedir.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Neden zayıf olay deseninin uygulanması?  
 Olayları dinlemek bellek sızıntılarına neden olabilir. Bir olayı dinlemek için tipik bir yöntem, bir kaynak üzerindeki olaya bir işleyici ekleyen dile özgü söz dizimini kullanmaktır. Örneğin, ' de C#, bu söz dizimi: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Bu teknik, olay kaynağından olay dinleyicisine güçlü bir başvuru oluşturur. Genellikle, bir dinleyici için bir olay işleyicisi iliştirmek, dinleyicinin, kaynağın nesne ömrü tarafından etkilenen bir nesne yaşam süresine sahip olmasına neden olur (olay işleyicisi açıkça kaldırılmadığı takdirde). Ancak belirli durumlarda, dinleyicinin nesne yaşam süresinin, uygulamanın yaşam süresine göre değil, uygulamanın görsel ağacına ait olup olmadığı gibi diğer faktörlere göre denetlenmesini isteyebilirsiniz. Kaynak nesne ömrü, dinleyicinin nesne ömrünü aşacak şekilde genişlediğinde, normal olay deseninin bir bellek sızıntısına yol açar: dinleyici, amaçlarından daha uzun bir süre etkin tutulur.  
  
 Zayıf olay deseninin bu bellek sızıntısı sorununu çözmek için tasarlanmıştır. Zayıf olay alanı, bir dinleyicinin bir olaya kaydolması gerektiğinde kullanılabilir, ancak dinleyici ne zaman kaydı kaldırılacak. Zayıf olay deseninin, kaynağın nesne ömrü, dinleyicinin yararlı nesne ömrünü aştığında de kullanılabilir. (Bu durumda, *yararlı* olarak sizin tarafınızdan belirlenir.) Zayıf olay deseninin, dinleyicinin herhangi bir şekilde nesne ömrü özelliklerini etkilemeden olay için kaydolmasına ve bu olayı almasına izin verir. Aslında, kaynaktan kapsanan başvuru, dinleyicinin çöp toplama için uygun olup olmadığını belirleyemez. Başvuru zayıf bir başvurudur, bu nedenle zayıf olay deseninin ve ilgili API 'lerin adlandırılması. Dinleyici atık olarak toplanamaz veya başka bir şekilde yok edilebilir ve kaynak olmayan işleyici başvurularını artık yok edilmiş bir nesneye korumadan devam edebilir.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Zayıf olay deseninin kim tarafından uygulanması gerekir?  
 Zayıf olay deseninin uygulanması, birincil olarak denetim yazarları için ilginç bir olaydır. Denetim yazarı olarak, denetiminizin davranışından ve kapsamasından büyük ölçüde sorumlu olursunuz ve onun eklendiği uygulamalarla ilgili etkileri vardır. Bu, özellikle açıklanan bellek sızıntısı sorununu işlemede denetim nesnesi ömrü davranışını içerir.  
  
 Belirli senaryolar doğal olarak zayıf olay deseninin uygulamasına ödünç vermez. Bu tür bir senaryo, veri bağlamadır. Veri bağlamada, kaynak nesnenin bağlama hedefi olan dinleyici nesnesinden tamamen bağımsız olması yaygındır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlamasının birçok yönü, olayların nasıl uygulandığı konusunda zayıf olay deseninin zaten uygulanmış olması.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Zayıf olay deseninin nasıl uygulanacağı  
 Zayıf olay deseninin uygulanması için üç yol vardır. Aşağıdaki tabloda üç yaklaşım listelenmekte ve her birini ne zaman kullanmanız gerektiği hakkında bazı rehberlik sunulmaktadır.  
  
|Uygulanabilecek|Ne zaman uygulanacağı|  
|--------------|-----------------------|  
|Varolan zayıf bir olay Yöneticisi sınıfını kullan|Abone olmak istediğiniz olaya karşılık gelen bir <xref:System.Windows.WeakEventManager>varsa, varolan zayıf olay yöneticisini kullanın. WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için <xref:System.Windows.WeakEventManager> sınıfında devralma hiyerarşisine bakın. Dahil edilen zayıf olay yöneticileri sınırlı olduğundan, muhtemelen diğer yaklaşımlardan birini seçmeniz gerekir.|  
|Genel bir zayıf olay Yöneticisi sınıfı kullanın|Mevcut bir <xref:System.Windows.WeakEventManager> kullanılabilir olmadığında genel <xref:System.Windows.WeakEventManager%602> kullanın, uygulamak için kolay bir yol ve verimlilik konusunda endişe istemezsiniz. Genel <xref:System.Windows.WeakEventManager%602>, var olan veya özel zayıf bir olay yöneticisinden daha az verimlidir. Örneğin, genel sınıf, olayın adı verilen olayı bulmaya yönelik daha fazla yansıma yapar. Ayrıca, genel <xref:System.Windows.WeakEventManager%602> kullanarak olayı kaydeden kod, var olan veya özel bir <xref:System.Windows.WeakEventManager>kullanmaktan daha ayrıntılıdır.|  
|Özel bir zayıf olay Yöneticisi sınıfı oluşturma|Mevcut bir <xref:System.Windows.WeakEventManager> kullanılabilir olmadığında ve en iyi verimliliği istediğinizde özel bir <xref:System.Windows.WeakEventManager> oluşturun. Bir olaya abone olmak için özel <xref:System.Windows.WeakEventManager> kullanmak daha verimli olacaktır, ancak başlangıçta daha fazla kod yazma maliyetine tabi olursunuz.|  
|Üçüncü taraf zayıf bir olay Yöneticisi kullanma|NuGet [birkaç zayıf olay yöneticilerine](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) sahiptir ve birçok WPF çerçevesi de (örneğin, [esnek olarak bağlanmış olay aboneliği ile ilgili belgelere](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)bakın).|

 Aşağıdaki bölümlerde, zayıf olay deseninin nasıl uygulanacağı açıklanır.  Bu tartışmanın amaçları doğrultusunda Abone olunacak olay aşağıdaki özelliklere sahiptir.  
  
- Olay adı `SomeEvent`.  
  
- Olay `EventSource` sınıfı tarafından tetiklenir.  
  
- Olay işleyicisinin türü: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).  
  
- Olay, olay işleyicilerine `SomeEventEventArgs` türünde bir parametre geçirir.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Var olan zayıf bir olay Yöneticisi sınıfını kullanma  
  
1. Var olan zayıf bir olay Yöneticisi bulun.  
  
     WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için <xref:System.Windows.WeakEventManager> sınıfında devralma hiyerarşisine bakın.  
  
2. Normal olay kancası yerine yeni zayıf olay yöneticisini kullanın.  
  
     Örneğin, kodunuz bir olaya abone olmak için aşağıdaki kalıbı kullanıyorsa:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Aşağıdaki düzene göre değiştirin:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuz bir olaydan aboneliği kaldırmak için aşağıdaki kalıbı kullanıyorsa:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Aşağıdaki düzene göre değiştirin:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Genel zayıf olay Yöneticisi sınıfını kullanma  
  
1. Normal olay kancası yerine genel <xref:System.Windows.WeakEventManager%602> sınıfını kullanın.  
  
     Olay dinleyicilerini kaydetmek için <xref:System.Windows.WeakEventManager%602> kullandığınızda, aşağıdaki kodda gösterildiği gibi, olay kaynağını ve <xref:System.EventArgs> türünü sınıfa tür parametreleri olarak ve <xref:System.Windows.WeakEventManager%602.AddHandler%2A> çağırın:  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Özel bir zayıf olay Yöneticisi sınıfı oluşturma  
  
1. Aşağıdaki sınıf şablonunu projenize kopyalayın.  
  
     Bu sınıf <xref:System.Windows.WeakEventManager> sınıfından devralır.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. `SomeEventWeakEventManager` adını kendi adınızla değiştirin.  
  
3. Daha önce açıklanan üç adı, olaylarınızın karşılık gelen adlarıyla değiştirin. (`SomeEvent`, `EventSource`ve `SomeEventEventArgs`)  
  
4. Zayıf olay Yöneticisi sınıfının görünürlüğünü (ortak/iç/özel), yönettiği olayla aynı görünürlüğe ayarlayın.  
  
5. Normal olay kancası yerine yeni zayıf olay yöneticisini kullanın.  
  
     Örneğin, kodunuz bir olaya abone olmak için aşağıdaki kalıbı kullanıyorsa:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Aşağıdaki düzene göre değiştirin:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Benzer şekilde, kodunuz bir olaya abonelik kaldırmak için aşağıdaki kalıbı kullanıyorsa:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Aşağıdaki düzene göre değiştirin:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
