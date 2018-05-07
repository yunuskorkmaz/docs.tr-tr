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
ms.openlocfilehash: fbd19591c260b0ad160339b45fd762e7a87bbc74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF Özel Denetiminin UI Otomasyonu
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] istemciler inceleyin ya da platformlar ve altyapıları çeşitli kullanıcı arabirimleri çalışmasına kullanabilir, Otomasyon tek, genelleştirilmiş bir arabirim sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] Kalite güvence (test) kod ve kullanıcı arabirimi öğeleri inceleyin ve diğer kodundan kullanıcı etkileşimi onlarla benzetimini yapmak ekran okuyucular gibi erişilebilirlik uygulamaları etkinleştirir. Hakkında bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] tüm platformlarda erişilebilirlik bakın.  
  
 Bu konuda, bir WPF uygulamasında çalışan özel bir denetim için sunucu tarafı UI Otomasyonu sağlayıcıyı uygulama açıklar. WPF destekleyen [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kullanıcı arabirimi öğeleri ağacının parallels eş Otomasyon nesne ağacının aracılığıyla. Sınama kodu ve erişilebilirlik özellikleri (işlemdeki kodunu) doğrudan Otomasyon eş nesneleri kullanabilir sağlayan uygulamalar tarafından sağlanan genelleştirilmiş arabirimi aracılığıyla veya [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Otomasyon eş sınıfları  
 WPF denetimleri Destek [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] öğesinden türetilen eş sınıfları ağacının aracılığıyla <xref:System.Windows.Automation.Peers.AutomationPeer>. Kural tarafından eş sınıf adları denetim sınıf adıyla başlar ve "AutomationPeer" ile bitmelidir. Örneğin, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> eş sınıfı olan <xref:System.Windows.Controls.Button> kontrol sınıfı. Eş sınıfları kabaca eşdeğerdir [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kontrol türleri ancak özgü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri. WPF uygulamaları aracılığıyla erişen Otomasyon kodu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] arabirimi Otomasyon eş doğrudan kullanmaz, ancak aynı işlem alanı Otomasyon kodda kullanabileceğiniz Otomasyon eş doğrudan.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Yerleşik Otomasyon eş sınıfları  
 Öğeleri, kullanıcı arabirimi etkinliğinden kabul ederse veya ekran okuyucusu uygulamalar kullanıcılar tarafından gerekli bilgileri içeriyorsa bir Otomasyon eş sınıfı uygulayın. Tüm WPF görsel öğeleri Otomasyon eş vardır. Otomasyon eş uygulayan sınıflar örnekleri <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, ve <xref:System.Windows.Controls.Label>. Otomasyon eş kullanılmaz sınıfları örnekleridir öğesinden türetilen sınıflar <xref:System.Windows.Controls.Decorator>, gibi <xref:System.Windows.Controls.Border>ve temel sınıfları <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.Canvas>.  
  
 Temel <xref:System.Windows.Controls.Control> sınıfı, karşılık gelen bir eş sınıfı yok. Türetilen özel bir denetim karşılık gelecek şekilde eş sınıfı gerekiyorsa <xref:System.Windows.Controls.Control>, özel eş sınıfından türetilmelidir <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Türetilen eşleri için güvenlik konuları  
 Otomasyon eşleri bir kısmi güven ortamında çalıştırmanız gerekir. UIAutomationClient bütünleştirilmiş kodda bir kısmi güven ortamında çalışacak şekilde yapılandırılmamış ve Otomasyon eş kod bu derleme başvuru vermemelisiniz. Bunun yerine, sınıfları UIAutomationTypes derlemede kullanmanız gerekir. Örneğin, kullanmanız gereken <xref:System.Windows.Automation.AutomationElementIdentifiers> karşılık gelen UIAutomationTypes derleme sınıfından <xref:System.Windows.Automation.AutomationElement> UIAutomationClient derlemede sınıfı. Otomasyon eş kodda UIAutomationTypes derleme başvurusu güvenlidir.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Eş gezinme  
 Bir Otomasyon eş bulunduktan sonra işlem kodu eş ağaç nesnenin çağırarak gidebilirsiniz <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> yöntemleri. Arasında gezinme [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] denetimin öğelerinin eşin uygulaması tarafından desteklenen <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> yöntemi. UI Otomasyonu sistem denetimi içinde yer alan alt ağacı oluşturmak için bu yöntemi çağırır; Örneğin, bir liste kutusu öğeleri listeler. Varsayılan <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> yöntemi Otomasyon eş ağacının yapı öğelerinin görsel ağaç erişir. Özel denetimler bilgileri iletmek veya kullanıcı etkileşimi izin veren öğelerinin Otomasyon eş Otomasyon istemcilerden alt öğelerine göstermek için bu yöntemi geçersiz kılın.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Türetilen bir eş özelleştirmelerindeki  
 Öğesinden türetilen tüm sınıflar <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> korumalı sanal yöntemi içeren <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF çağrıları <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> her denetim için Otomasyon eş nesnesi alınamıyor. Otomasyon kodu eş bir denetimin özelliklerini ve özellikler hakkında bilgi almak için ve etkileşimli kullanım benzetimini yapmak için kullanabilirsiniz. Otomasyon destekleyen özel bir denetim geçersiz kılmanız gerekir <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> ve türeyen bir sınıf örneği dönmek <xref:System.Windows.Automation.Peers.AutomationPeer>. Örneğin, bir özel denetim türetilen <xref:System.Windows.Controls.Primitives.ButtonBase> sınıfı sonra tarafından döndürülen nesne <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> öğesinden türetilmelidir <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Özel bir denetim uygularken, benzersiz ve özel denetim için belirli bir davranışı açıklamak "Çekirdek" yöntemleri taban otomasyonu eş sınıfından geçersiz kılmanız gerekir.  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer geçersiz kıl  
 Geçersiz kılma <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> onun doğrudan veya dolaylı olarak öğesinden türetilmelidir, sağlayıcı nesnesi döndürecek şekilde özel denetim için yöntem <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>GetPattern geçersiz kıl  
 Otomasyon eş basitleştirmek bazı sunucu-tarafı uygulaması yönlerini [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar, ancak özel denetim Otomasyon eş gerekir hala işlemek düzeni arabirimleri. WPF olmayan sağlayıcıları gibi eş arabirimlerde uygulamaları sağlayarak denetim düzenleri desteği <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> ad alanı, gibi <xref:System.Windows.Automation.Provider.IInvokeProvider>. Denetim düzeni arabirimleri eş veya başka bir nesne tarafından uygulanabilir. Eşin uyarlamasını <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> belirtilen deseni destekleyen bir nesne döndürür. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kod çağrıları <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi ve belirten bir <xref:System.Windows.Automation.Peers.PatternInterface> numaralandırma değeri. Geçersiz kılma, <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> belirtilen desenle uygulayan nesnenin döndürmelidir. Denetiminizi desenin özel bir uygulama yoksa temel türün uyarlamasını çağırabilirsiniz <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> düzeni bu denetim türü için desteklenmiyorsa, uygulama veya null alınamadı. Örneğin, Özel NumericUpDown denetimi bir aralık içinde bir değere ayarlanabilir şekilde kendi [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] eş uygulamak <xref:System.Windows.Automation.Provider.IRangeValueProvider> arabirimi. Aşağıdaki örnekte gösterildiği nasıl eşin <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yanıtlamak için yöntem geçersiz bir <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> değeri.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi bir desen sağlayıcısı olarak bir alt öğe de belirtebilirsiniz. Aşağıdaki kodda gösterildiği nasıl <xref:System.Windows.Controls.ItemsControl> aktarımları kaydırın eş kendi iç düzeni işleme <xref:System.Windows.Controls.ScrollViewer> denetim.  
  
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
  
 Desen işleme için bir alt öğe belirtmek için bu kodu alt nesneyi alır, bir eş kullanarak oluşturur <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> yöntemi, ayarlar <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> yeni eşler arası geçerli, özellik ve yeni eş döndürür. Ayarı <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> Otomasyon eş ağacında görünmesini alt öğe üzerinde bir alt öğe engeller ve alt öğe tarafından oluşturulan tüm olaylara atar belirtilen denetim kaynaklanan olarak <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Denetim Otomasyon ağacında görünmez ve bunu oluşturan kaydırma olaylar görünür kaynaklanan için <xref:System.Windows.Controls.ItemsControl> nesnesi.  
  
### <a name="override-core-methods"></a>"Çekirdek" yöntemleri geçersiz kılın  
 Otomasyon kodu eş sınıfı genel yöntemini çağırarak denetiminizi hakkındaki bilgileri alır. Denetim hakkında bilgi sağlamak için Denetim uygulamanızı taban otomasyonu eş sınıfı tarafından sağlanan kopyanın farklı olduğu durumlarda adı "Çekirdek" ile biten her yöntemini geçersiz kılın. En azından denetiminizi uygulamalıdır <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> aşağıdaki örnekte gösterildiği gibi yöntemleri.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Uygulamanıza <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> döndürerek denetiminizi açıklar bir <xref:System.Windows.Automation.ControlType> değeri. Geri dönebilirsiniz rağmen <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, doğru şekilde denetiminizi tanımlarsa daha ayrıntılı denetim türlerinden birini döndürmelidir. Dönüş değeri <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> uygulamak sağlayıcı için ek iş gerektirir [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], ve [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] istemci ürünleri denetim yapısını, klavye etkileşimi ve olası denetim düzenleri düşündüğünüz alamadı.  
  
 Uygulama <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> denetiminizi veri içeriği veya etkileşimli bir kullanıcı arabirimi (veya her ikisi de) rolünde karşılayan göstermek için yöntemlerini. Varsayılan olarak, her iki yöntem dönmek `true`. Bu ayarları Otomasyon araçları Otomasyon ağacı filtre uygulamak için bu yöntemleri kullanabilir ekran okuyucular gibi kullanılabilirliğini artırır. Varsa, <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> bir alt öğe eşin için alt öğe eş işleme yöntemi aktarımları düzeni <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi Otomasyon ağacı alt eşten gizlemek için false dönebilirsiniz. Örneğin, kaydırma bir <xref:System.Windows.Controls.ListBox> tarafından işlenen bir <xref:System.Windows.Controls.ScrollViewer>ve Otomasyon eş için <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> tarafından döndürülen <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> yöntemi <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> ile ilişkili <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Bu nedenle, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> döndürür `false`, böylece <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> Otomasyon ağacında görünmez.  
  
 Otomasyon eş uygun varsayılan değerleri için Denetim sağlamalıdır. Not ekleyerek denetiminizi başvuran XAML çekirdek yöntemleri, eş uygulamaları kılabilirsiniz <xref:System.Windows.Automation.AutomationProperties> öznitelikleri. Örneğin, aşağıdaki XAML iki özelleştirilmiş sahip bir düğme oluşturur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Uygulama düzeni sağlayıcıları  
 Doğrudan sahip olan öğe türetilen, özel bir sağlayıcı tarafından uygulanan arabirimler açıkça bildirilir <xref:System.Windows.Controls.Control>. Örneğin, aşağıdaki kod bir eş için bildirir bir <xref:System.Windows.Controls.Control> bir aralık değeri uygular.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Sahibi olan denetimi gibi belirli bir denetim türünden türetilen varsa <xref:System.Windows.Controls.Primitives.RangeBase>, eş bir eşdeğer türetilmiş eş sınıfından türetilmiş olmalıdır. Bu durumda, gelen eş türetin <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, temel bir uyarlamasını sağladığı <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Aşağıdaki kod, bu tür bir eş bildirimi gösterir.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Bir örnek için bkz: [tema ve UI Otomasyon desteği örnek ile NumericUpDown özel denetimi](http://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Olayları Yükselt  
 Otomasyon istemcileri Otomasyon olaylarına abone olabilir. Özel denetimler çağırarak durumunu denetlemek için değişiklikleri rapor gerekir <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> yöntemi. Benzer şekilde, bir özellik değeri değiştiğinde, çağrı <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> yöntemi. Aşağıdaki kod, denetim kodu içinde eş nesnesinden alın ve bir olay yükseltmek için bir yöntem çağrısı gösterilmektedir. Bir iyileştirme kodu, bu olay türü için tüm dinleyiciler olup olmadığını belirler. Yalnızca dinleyicileri olduğunuzda olayı tetiklenmeden gereksiz yüke engel olan ve yanıt verebilir durumda kalması denetlenmesine yardımcı olur.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonuna Genel Bakış](../../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Tema ve UI Otomasyon desteği örnek ile NumericUpDown özel denetimi](http://go.microsoft.com/fwlink/?LinkID=160025)  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
