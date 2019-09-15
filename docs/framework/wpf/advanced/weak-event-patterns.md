---
title: Zayıf Olay Desenleri
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991797"
---
# <a name="weak-event-patterns"></a>Zayıf Olay Desenleri
Uygulamalarda, olay kaynaklarına eklenmiş olan işleyiciler, işleyiciyi kaynağa bağlayan dinleyici nesnesiyle birlikte yok edilmez. Bu durum bellek sızıntılarına neden olabilir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], belirli olaylar için adanmış bir yönetici sınıfı sağlayarak ve bu olay için dinleyicilerine bir arabirim uygulayarak bu sorunu gidermek için kullanılabilecek bir tasarım kalıbı sunar. Bu tasarım deseninin *zayıf olay deseninin*olduğu bilinmektedir.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Neden zayıf olay deseninin uygulanması?  
 Olayları dinlemek bellek sızıntılarına neden olabilir. Bir olayı dinlemek için tipik bir yöntem, bir kaynak üzerindeki olaya bir işleyici ekleyen dile özgü söz dizimini kullanmaktır. Örneğin, ' de C#, söz dizimi: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Bu teknik, olay kaynağından olay dinleyicisine güçlü bir başvuru oluşturur. Genellikle, bir dinleyici için bir olay işleyicisi iliştirmek, dinleyicinin, kaynağın nesne ömrü tarafından etkilenen bir nesne yaşam süresine sahip olmasına neden olur (olay işleyicisi açıkça kaldırılmadığı takdirde). Ancak belirli durumlarda, dinleyicinin nesne yaşam süresinin, uygulamanın yaşam süresine göre değil, uygulamanın görsel ağacına ait olup olmadığı gibi diğer faktörlere göre denetlenmesini isteyebilirsiniz. Kaynak nesne ömrü, dinleyicinin nesne ömrünü aşacak şekilde genişlediğinde, normal olay deseninin bir bellek sızıntısına yol açar: dinleyici, amaçlarından daha uzun bir süre etkin tutulur.  
  
 Zayıf olay deseninin bu bellek sızıntısı sorununu çözmek için tasarlanmıştır. Zayıf olay alanı, bir dinleyicinin bir olaya kaydolması gerektiğinde kullanılabilir, ancak dinleyici ne zaman kaydı kaldırılacak. Zayıf olay deseninin, kaynağın nesne ömrü, dinleyicinin yararlı nesne ömrünü aştığında de kullanılabilir. (Bu durumda, *yararlı* olarak sizin tarafınızdan belirlenir.) Zayıf olay deseninin, dinleyicinin herhangi bir şekilde nesne ömrü özelliklerini etkilemeden olay için kaydolmasına ve bu olayı almasına izin verir. Aslında, kaynaktan kapsanan başvuru, dinleyicinin çöp toplama için uygun olup olmadığını belirleyemez. Başvuru zayıf bir başvurudur, bu nedenle zayıf olay deseninin ve ilgili API 'lerin adlandırılması. Dinleyici atık olarak toplanamaz veya başka bir şekilde yok edilebilir ve kaynak olmayan işleyici başvurularını artık yok edilmiş bir nesneye korumadan devam edebilir.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Zayıf olay deseninin kim tarafından uygulanması gerekir?  
 Zayıf olay deseninin uygulanması, birincil olarak denetim yazarları için ilginç bir olaydır. Denetim yazarı olarak, denetiminizin davranışından ve kapsamasından büyük ölçüde sorumlu olursunuz ve onun eklendiği uygulamalarla ilgili etkileri vardır. Bu, özellikle açıklanan bellek sızıntısı sorununu işlemede denetim nesnesi ömrü davranışını içerir.  
  
 Belirli senaryolar doğal olarak zayıf olay deseninin uygulamasına ödünç vermez. Bu tür bir senaryo, veri bağlamadır. Veri bağlamada, kaynak nesnenin bağlama hedefi olan dinleyici nesnesinden tamamen bağımsız olması yaygındır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Veri bağlamasının birçok yönü, olayların nasıl uygulandığı konusunda zayıf olay deseninin zaten uygulanmış olması.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Zayıf olay deseninin nasıl uygulanacağı  
 Zayıf olay deseninin uygulanması için üç yol vardır. Aşağıdaki tabloda üç yaklaşım listelenmekte ve her birini ne zaman kullanmanız gerektiği hakkında bazı rehberlik sunulmaktadır.  
  
|Yaklaşım|Ne zaman uygulanacağı|  
|--------------|-----------------------|  
|Varolan zayıf bir olay Yöneticisi sınıfını kullan|Abone olmak istediğiniz olaya karşılık gelen <xref:System.Windows.WeakEventManager>varsa, var olan zayıf olay yöneticisini kullanın. WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için, <xref:System.Windows.WeakEventManager> sınıfındaki devralma hiyerarşisine bakın. Dahil edilen zayıf olay yöneticileri sınırlı olduğundan, muhtemelen diğer yaklaşımlardan birini seçmeniz gerekir.|  
|Genel bir zayıf olay Yöneticisi sınıfı kullanın|<xref:System.Windows.WeakEventManager%602> Mevcut<xref:System.Windows.WeakEventManager> olmadığında genel ' i kullanın, uygulanması kolay bir yol istersiniz ve verimlilik konusunda endişe etmeniz gerekmez. Genel <xref:System.Windows.WeakEventManager%602> , mevcut veya özel zayıf bir olay yöneticisinden daha az verimlidir. Örneğin, genel sınıf, olayın adı verilen olayı bulmaya yönelik daha fazla yansıma yapar. Ayrıca, genel <xref:System.Windows.WeakEventManager%602> kullanılarak olayı kaydeden kod, var olan veya özel <xref:System.Windows.WeakEventManager>kullanmaktan daha ayrıntılıdır.|  
|Özel bir zayıf olay Yöneticisi sınıfı oluşturma|<xref:System.Windows.WeakEventManager> Mevcut<xref:System.Windows.WeakEventManager> olmadığında ve en iyi verimliliği istediğinizde bir özel oluşturun. Bir olaya abone <xref:System.Windows.WeakEventManager> olmak için özel kullanmak daha verimli olacaktır, ancak başlangıçta daha fazla kod yazma maliyetine tabi olursunuz.|  
|Üçüncü taraf zayıf bir olay Yöneticisi kullanma|NuGet [birkaç zayıf olay yöneticilerine](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) sahiptir ve birçok WPF çerçevesi de (örneğin, [esnek olarak bağlanmış olay aboneliği ile ilgili belgelere](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)bakın).|

 Aşağıdaki bölümlerde, zayıf olay deseninin nasıl uygulanacağı açıklanır.  Bu tartışmanın amaçları doğrultusunda Abone olunacak olay aşağıdaki özelliklere sahiptir.  
  
- Olay adı `SomeEvent`.  
  
- Olay, `EventSource` sınıfı tarafından tetiklenir.  
  
- Olay işleyicisinin türü: `SomeEventEventHandler` (veya `EventHandler<SomeEventEventArgs>`).  
  
- Olay, olay işleyicilere türünde `SomeEventEventArgs` bir parametre geçirir.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Var olan zayıf bir olay Yöneticisi sınıfını kullanma  
  
1. Var olan zayıf bir olay Yöneticisi bulun.  
  
     WPF 'e dahil olan zayıf olay yöneticilerinin bir listesi için, <xref:System.Windows.WeakEventManager> sınıfındaki devralma hiyerarşisine bakın.  
  
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
  
1. Normal olay kancası <xref:System.Windows.WeakEventManager%602> yerine genel sınıfı kullanın.  
  
     Olay dinleyicilerini <xref:System.Windows.WeakEventManager%602> kaydetmek için kullandığınızda, aşağıdaki kodda gösterildiği gibi, olay kaynağını <xref:System.EventArgs> ve türü sınıf için tür parametreleri olarak girin ve çağırın <xref:System.Windows.WeakEventManager%602.AddHandler%2A> :  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Özel bir zayıf olay Yöneticisi sınıfı oluşturma  
  
1. Aşağıdaki sınıf şablonunu projenize kopyalayın.  
  
     Bu sınıf <xref:System.Windows.WeakEventManager> sınıfından devralır.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. `SomeEventWeakEventManager` Adı kendi adınızla değiştirin.  
  
3. Daha önce açıklanan üç adı, olaylarınızın karşılık gelen adlarıyla değiştirin. (`SomeEvent`, `EventSource`, ve `SomeEventEventArgs`)  
  
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
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
