---
title: WPF Özel Denetiminin UI Otomasyonu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: 0d663acc195b36fdc95c196f2233ae997fbd9195
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132775"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF Özel Denetiminin UI Otomasyonu
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] istemciler, platformlar ve altyapıları çeşitli kullanıcı arabirimleri başlatılmayabilir veya incelemek için kullanabilir, Otomasyon tek, genelleştirilmiş bir arabirim sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] Kalite güvencesi (test) kod hem kullanıcı arabirimi öğeleri incelenir ve diğer koddan onlarla kullanıcı etkileşiminin benzetimini ekran okuyucular gibi erişilebilirlik uygulamaları etkinleştirir. Hakkında bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] erişilebilirlik tüm platformlarda bakın.  
  
 Bu konu, bir WPF uygulamasında çalışan özel bir denetim için sunucu tarafı UI Otomasyonu sağlayıcıyı uygulama açıklar. WPF destekler [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] ağacı kullanıcı arabirimi öğelerinin parallels eş Otomasyon nesne ağacının aracılığıyla. Test kodu ve erişilebilirlik özellikleri (işlem içi kodunu) doğrudan Otomasyon eş nesneleri kullanabilirsiniz sağlayan uygulamalar veya sağlanan genelleştirilmiş arabirimi aracılığıyla [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Otomasyon eş sınıfları  
 WPF denetimlerini Destek [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] eş sınıfların türetilmesi ağacı yoluyla <xref:System.Windows.Automation.Peers.AutomationPeer>. Kural olarak, eş sınıf adları denetim sınıfı adı ile başlayan ve "AutomationPeer" ile bitmelidir. Örneğin, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> eş sınıfı olan <xref:System.Windows.Controls.Button> denetim sınıfı. Eş sınıflardır kabaca [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerinin ancak özgü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri. WPF uygulamaları aracılığıyla erişen otomasyon kodunuzu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] arabirimi Otomasyon eşleri doğrudan kullanmaz, ancak aynı işlem alanında Otomasyon kodunu kullanabilir Otomasyon eşleri doğrudan.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Yerleşik Otomasyon eş sınıfları  
 Öğeleri bir Otomasyon eş sınıfı, kullanıcı arabirimi etkinliği kabul veya uygulamaların kullanıcılarına, ekran okuyucusu tarafından gerekli bilgileri içerirler uygulayın. Tüm WPF görsel öğeleri Otomasyon eşleri vardır. Otomasyon eşleri uygulayan sınıflar örnekler <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, ve <xref:System.Windows.Controls.Label>. Örnekler Otomasyon eşleri uygulamayan sınıflar türetilen sınıfları <xref:System.Windows.Controls.Decorator>, gibi <xref:System.Windows.Controls.Border>ve temel sınıfları <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.Canvas>.  
  
 Temel <xref:System.Windows.Controls.Control> sınıfı, karşılık gelen bir eş sınıfı yok. Öğesinden türetilen özel bir denetim değerine karşılık gelen bir eş sınıf gerekiyorsa <xref:System.Windows.Controls.Control>, özel eş sınıftan türetilmelidir <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Türetilmiş eşleri için güvenlik konuları  
 Otomasyon eşleri, kısmi güven ortamında çalıştırmanız gerekir. Kod UIAutomationClient derlemedeki bir kısmi güven ortamında çalıştırmak için yapılandırılmamış ve Otomasyon eş kod derlemeye başvurmamalıdır. Bunun yerine, UIAutomationTypes derlemede sınıfları kullanmanız gerekir. Örneğin, kullanmanız gereken <xref:System.Windows.Automation.AutomationElementIdentifiers> sınıfı karşılık gelen UIAutomationTypes derlemesinden <xref:System.Windows.Automation.AutomationElement> UIAutomationClient derlemede sınıfı. Otomasyon eş kod UIAutomationTypes derlemeye başvurmak güvenlidir.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Eş Gezinti  
 Bir Otomasyon eş bulunduktan sonra işlem içi kod eş ağaç nesnenin çağırarak gidebilirsiniz <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> yöntemleri. Arasında gezinme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] denetimin öğelerinin eşin uygulaması tarafından desteklenen <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> yöntemi. UI Otomasyon sistemi oluşturan bir denetimi içinde bulunan alt ağacı oluşturmak için bu yöntemi çağırır; Örneğin, bir liste kutusunda öğeleri listelenir. Varsayılan <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> yöntemi, Otomasyon eşleri ağacını oluşturmak için öğelerin görsel ağaç'ten gönderilir. Özel denetimler alt öğeleri Otomasyon eşleri bilgileri iletmek veya kullanıcı etkileşimi izin veren öğeleri döndürmek, Otomasyon istemcilerine kullanıma sunmak için bu yöntemi yok sayın.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Türetilen bir eş özelleştirmeleri  
 Öğesinden türetilen tüm sınıflar <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> korumalı sanal yöntem içeren <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF çağrıları <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> her denetim için Otomasyon eş nesnesi alınamıyor. Otomasyon kodunuzu eş bir denetimin özelliklerini ve özellikleri hakkında bilgi edinin ve etkileşimli kullanım benzetimini yapmak için kullanabilirsiniz. Otomasyon destekleyen özel bir denetim kılmalı <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> ve türeyen bir sınıf örneği dönüş <xref:System.Windows.Automation.Peers.AutomationPeer>. Örneğin, bir özel denetim türetildiği <xref:System.Windows.Controls.Primitives.ButtonBase> sınıfı sonra tarafından döndürülen nesne <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> türetilmesi <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Özel denetim uygularken temel Otomasyon eş sınıfından benzersiz ve özel denetiminizi özgü davranışı açıklamak "Çekirdek" yöntemleri geçersiz kılmanız gerekir.  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer geçersiz kıl  
 Geçersiz kılma <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> yöntemi doğrudan veya dolaylı olarak öğesinden türetilmelidir sağlayıcısı nesnenizin BT'nin döndürecek şekilde özel denetiminizin <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>GetPattern geçersiz kıl  
 Otomasyon eşleri basitleştirmek bazı sunucu-tarafı uygulaması yönlerini [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar, ancak özel denetim Otomasyon eşleri gerekir hala işleme düzeni arabirimleri. WPF olmayan sağlayıcıları gibi arabirimlerde uygulamaları sağlayarak eşleri denetim düzenleri desteği <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> ad gibi <xref:System.Windows.Automation.Provider.IInvokeProvider>. Denetim düzeni arabirimleri eş veya başka bir nesne tarafından uygulanabilir. Eşin uygulaması <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> belirtilen deseni destekleyen bir nesne döndürür. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kod çağrıları <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi ve belirten bir <xref:System.Windows.Automation.Peers.PatternInterface> numaralandırma değeri. Kılacağınızı <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> belirtilen desenle uygulayan nesnenin döndürmelidir. Denetim özel bir uygulama bir desenin sahip değilse temel türün uygulamasını çağırabilirsiniz <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> düzeni için bu denetim türü desteklenmiyorsa, uygulama veya null alınacak. Örneğin, özel bir NumericUpDown denetimi bir aralıkta bir değer ayarlanabilir şekilde kendi [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] eş uygulamak <xref:System.Windows.Automation.Provider.IRangeValueProvider> arabirimi. Aşağıdaki örnekte gösterildiği nasıl eşin <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi geçersiz kılınmıştır yanıt vermek için bir <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> değeri.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi bir alt öğe bir desen sağlayıcısı olarak belirtebilirsiniz. Aşağıdaki kodda gösterildiği nasıl <xref:System.Windows.Controls.ItemsControl> aktarımları deseni işleme eş bilgisayara, iç kaydırma <xref:System.Windows.Controls.ScrollViewer> denetimi.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Desen işleme için bir alt öğe belirtmek için bu kodu alt nesneyi alır, bir eş kullanarak oluşturur <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> yöntemini ayarlar <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> yeni eşler arası geçerli, özelliği ve yeni eş döndürür. Ayarı <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> üzerinde bir alt öğe alt öğe Otomasyon eş ağacında görüntülenmesini önler ve alt öğe tarafından oluşturulan tüm olayları atar belirtilen denetim kaynaklanan olarak <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Denetimi Otomasyon ağacında görünmez ve ürettiği kaydırma olayları kaynaklanan görünüyor <xref:System.Windows.Controls.ItemsControl> nesne.  
  
### <a name="override-core-methods"></a>"Çekirdek" yöntemleri geçersiz kılın  
 Otomasyon kodunuzu, genel eş sınıfı yöntemleri çağırarak denetiminiz hakkındaki bilgileri alır. Denetim hakkında bilgi sağlamak için temel Otomasyon eş sınıfı tarafından sağlanan, Denetim uygulamanız farklıdır, adı "Çekirdek" ile biten her yöntemi yok sayın. En az denetiminiz uygulamalıdır <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> yöntemleri, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Uygulamanıza <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> döndürerek denetiminiz açıklar bir <xref:System.Windows.Automation.ControlType> değeri. İade edebilirsiniz ancak <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, doğru bir şekilde denetiminiz tanımlıyorsa daha ayrıntılı denetim türlerinden birini döndürmelidir. Dönüş değeri <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> uygulamak sağlayıcı için fazladan iş gerektirir [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], ve [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] istemci ürünleri denetim yapısı, klavye etkileşim ve olası denetim desenlerini tahmin oluşturulamıyor.  
  
 Uygulama <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> denetiminiz veri içeriği veya etkileşimli bir kullanıcı arabirimi (veya her ikisi) rolünde karşıladığı göstermek için yöntemleri. Varsayılan olarak, her iki yöntem dönüş `true`. Bu ayarlar, Otomasyon araçları gibi Otomasyon ağacı filtrelemek için bu yöntemleri kullanabilir ekran okuyucular, kullanılabilirliğini artırın. Varsa, <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> yöntemi aktarımları deseni bir alt öğe eşin için alt öğe eş işleme <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi Otomasyon ağacı alt öğe eşten gizlemek için false olarak döndürebilir. Örneğin, kaydırma bir <xref:System.Windows.Controls.ListBox> tarafından işlenen bir <xref:System.Windows.Controls.ScrollViewer>ve Otomasyon eş için <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> tarafından döndürülen <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> yöntemi <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> ilişkili <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Bu nedenle, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> döndürür `false`, böylece <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> Otomasyon ağaçta görünür değil.  
  
 Otomasyon eşdüzey, denetim için uygun varsayılan değerler sağlamanız gerekir. Not ekleyerek denetiminiz başvuran XAML çekirdek yöntemleri, eş uygulamaları kılabilirsiniz <xref:System.Windows.Automation.AutomationProperties> öznitelikleri. Örneğin, aşağıdaki XAML iki özelleştirilmiş bir düğme oluşturur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Uygulama düzeni sağlayıcıları  
 Sahip olan öğeyi doğrudan türetilen, özel bir sağlayıcı tarafından uygulanan arabirimler açıkça bildirilen <xref:System.Windows.Controls.Control>. Örneğin, aşağıdaki kod bir eşdüzey hizmet sağlayıcı için bildirir bir <xref:System.Windows.Controls.Control> uygulayan bir aralık değeri.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Sahip olan denetimi gibi belirli bir denetim türünden türetilen varsa <xref:System.Windows.Controls.Primitives.RangeBase>, eş bir eşdeğer türetilmiş eş sınıfından türetilir. Bu durumda, eş öğesinden türetin <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, bir taban uygulamasını sağladığı <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Aşağıdaki kod, bu tür bir eş bildirimi gösterir.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Bir örnek için bkz: [NumericUpDown özel denetim teması ve UI Otomasyon desteği örnek](https://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Olay  
 Otomasyon istemcileri Otomasyon olaylarına abone olabilirsiniz. Özel denetimler çağırarak durumunu denetlemek için değişiklikleri rapor gerekir <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> yöntemi. Benzer şekilde, bir özellik değeri değiştiğinde, çağrı <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> yöntemi. Aşağıdaki kod, denetim kodu içinde eş nesnesinden alın ve olay oluşturmak için bir yöntem çağırmak nasıl gösterir. Bir iyileştirme kodu, bu olay türü için bir dinleyici olup olmadığını belirler. Olayı dinleyicilerini olduğunda, gereksiz yükünü ortadan kaldırır ve denetimin yanıt verebilir durumda kalmasına yardımcı olur.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](../../ui-automation/ui-automation-overview.md)
- [NumericUpDown özel denetim teması ve UI Otomasyon desteği örneği](https://go.microsoft.com/fwlink/?LinkID=160025)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../ui-automation/server-side-ui-automation-provider-implementation.md)
