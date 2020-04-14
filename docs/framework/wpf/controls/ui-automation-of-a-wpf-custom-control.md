---
title: Özel Kontrolün Kullanıcı Aracı Otomasyonu
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
ms.openlocfilehash: 97db94215220ac2a68e0395bd63b7a874a745a48
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243251"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF Özel Denetiminin UI Otomasyonu
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]otomasyon istemcilerinin çeşitli platform ve çerçevelerin kullanıcı arabirimlerini incelemek veya çalıştırmak için kullanabilecekleri tek ve genelleştirilmiş bir arayüz sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]hem kalite güvencesi (test) kodu hem de ekran okuyucular gibi erişilebilirlik uygulamalarının kullanıcı arabirimi öğelerini incelemesini ve kullanıcı etkileşimini diğer kodlardan simüle etmesini sağlar. Tüm platformlar [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] hakkında bilgi için Erişilebilirlik'e bakın.  
  
 Bu konu, wpf uygulamasında çalışan özel bir denetim için sunucu tarafındaki bir Kullanıcı Arabirimi Otomasyon sağlayıcısının nasıl uygulanacağını açıklar. WPF, [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kullanıcı arabirimi öğeleri ağacına paralel eş otomasyon nesneleri ağacı aracılığıyla destekler. Erişilebilirlik özellikleri sağlayan test kodu ve uygulamaları, otomasyon eş nesnelerini doğrudan (işlem kodu için) [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]veya tarafından sağlanan genelleştirilmiş arabirim aracılığıyla kullanabilir.  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>Otomasyon Akran Sınıfları  
 WPF, [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] desteği, 'den <xref:System.Windows.Automation.Peers.AutomationPeer>türeyen eş sınıfları ağacı aracılığıyla denetler. Kural kuralına göre, eş sınıf adları denetim sınıfı adı ile başlar ve "AutomationPeer" ile sona erer. Örneğin, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> denetim sınıfının <xref:System.Windows.Controls.Button> eş sınıfıdır. Eş sınıfları kabaca [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerine eşdeğerdir, ancak WPF öğelerine özgür. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] WPF uygulamalarına arayüz üzerinden erişen otomasyon kodu doğrudan otomasyon eşlerini kullanmaz, ancak aynı işlem alanındaki otomasyon kodu otomasyon eşlerini doğrudan kullanabilir.  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>Dahili Otomasyon Eş Sınıfları  
 Öğeler, kullanıcıdan arabirim etkinliğini kabul ettiklerinde veya ekran okuyucu uygulamalarının kullanıcıları tarafından gerekli bilgileri içeriyorsa bir otomasyon eş sınıfı uygular. Tüm WPF görsel öğeleri otomasyon eşesahiptir. Otomasyon eşlerini uygulayan sınıflara <xref:System.Windows.Controls.TextBox>örnek <xref:System.Windows.Controls.Label>olarak <xref:System.Windows.Controls.Button>, ve . Otomasyon eşlerini uygulamayan <xref:System.Windows.Controls.Decorator>sınıflara örnek <xref:System.Windows.Controls.Border>olarak, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> ", " gibi , ve <xref:System.Windows.Controls.Canvas>.  
  
 Taban <xref:System.Windows.Controls.Control> sınıfın karşılık gelen bir eş sınıfı yok. Türeyen özel bir denetime karşılık gelecek bir <xref:System.Windows.Controls.Control>eş sınıfına ihtiyacınız varsa, <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>özel eş sınıfını .  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>Türemiş Eşler için Güvenlik Hususları  
 Otomasyon eşarkadaşları kısmi güven ortamında çalışmalıdır. UIAutomationClient derlemesindeki kod kısmi güven ortamında çalışacak şekilde yapılandırılmamıştır ve otomasyon eş kodu bu derlemeye başvurmamalıdır. Bunun yerine, UIAutomationTypes derlemesindeki sınıfları kullanmanız gerekir. Örneğin, UIAutomationTypes <xref:System.Windows.Automation.AutomationElementIdentifiers> derlemesindeki sınıfı kullanmanız gerekir, bu <xref:System.Windows.Automation.AutomationElement> da UIAutomationClient derlemesindeki sınıfa karşılık gelir. Otomasyon eş kodunda UIAutomationTypes derlemesine başvurmak güvenlidir.  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>Eş Navigasyon  
 Bir otomasyon eşini buladıktan sonra, işlem kodu nesnenin <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> yöntemlerini çağırarak eş ağacında gezinebilir. Bir denetim içinde WPF elemanları arasında gezinme <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> yöntemin eşin uygulanması tarafından desteklenir. UI Otomasyon sistemi, bir denetim içinde bulunan alt öğelerden oluşan bir ağaç oluşturmak için bu yöntemi çağırır; örneğin, liste kutusundaki öğeleri listeleyin. Varsayılan <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> yöntem, otomasyon eşlerinden oluşan ağacı oluşturmak için öğelerin görsel ağacından geçer. Özel denetimler, küçük öğeleri otomasyon istemcilerine maruz bırakmak için bu yöntemi geçersiz kılar, bilgi aktaran veya kullanıcı etkileşimine izin veren öğelerin otomasyon eşlerini döndürür.  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>Türemiş Eş'te Özelleştirmeler  
 Korunan sanal yöntemden <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> <xref:System.Windows.ContentElement> türeyen ve içeren tüm sınıflar. WPF, <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> her denetim için otomasyon eş nesnesini almak için çağrıda bulunur. Otomasyon kodu, bir denetimin özellikleri ve özellikleri hakkında bilgi almak ve etkileşimli kullanımı simüle etmek için eş'i kullanabilir. Otomasyonu destekleyen özel bir <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> denetim geçersiz kılınmalı ve bir sınıfın <xref:System.Windows.Automation.Peers.AutomationPeer>örneğini döndürmelidir. Örneğin, özel bir denetim <xref:System.Windows.Controls.Primitives.ButtonBase> sınıftan türetilmiştir, o <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> zaman tarafından <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>döndürülen nesne.  
  
 Özel denetim uygularken, özel denetiminize özgü ve özgün davranışları açıklayan taban otomasyon eş sınıfından "Çekirdek" yöntemlerini geçersiz kılmanız gerekir.  
  
### <a name="override-oncreateautomationpeer"></a>Override OnCreateAutomationPeer  
 Özel denetiminiz için <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> yöntemi geçersiz kılın, böylece sağlayıcı nesnenizi döndürecek <xref:System.Windows.Automation.Peers.AutomationPeer>ve bu yöntem doğrudan veya dolaylı olarak .  
  
### <a name="override-getpattern"></a>GetPattern'i Geçersiz Kılın  
 Otomasyon eşler, sunucu tarafındaki [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıların bazı uygulama yönlerini basitleştirir, ancak özel denetim otomasyonu eşler desen arabirimlerini işlemeye devam etmelidir. WPF olmayan sağlayıcılar gibi, eşler de <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> ad alanında arabirimlerin uygulamalarını sağlayarak <xref:System.Windows.Automation.Provider.IInvokeProvider>denetim desenlerini destekler. Denetim deseni arabirimleri eşin kendisi veya başka bir nesne tarafından uygulanabilir. Eşin <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> uygulaması, belirtilen deseni destekleyen nesneyi döndürür. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]kod <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi çağırır ve numaralandırma <xref:System.Windows.Automation.Peers.PatternInterface> değeri belirtir. Geçersiz kılmanız, belirtilen deseni uygulayan nesneyi <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> döndürmelidir. Denetiminizde bir desenin özel bir uygulaması yoksa, bu denetim türü <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> için desteklenmiyorsa, temel türün uygulanmasını almak için uygulanmasını veya deseni geçersiz kılmayı çağırabilirsiniz. Örneğin, özel bir SayısalUpDown denetimi bir aralık içinde bir değere [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] ayarlanabilir, <xref:System.Windows.Automation.Provider.IRangeValueProvider> böylece eş arabirimi uygular. Aşağıdaki örnek, eşin <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yönteminin bir <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> değere yanıt vermek için nasıl geçersiz kılındığını gösterir.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Bir <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntem de desen sağlayıcısı olarak bir alt öğe belirtebilirsiniz. Aşağıdaki kod, <xref:System.Windows.Controls.ItemsControl> kaydırma deseni işlemeyi iç <xref:System.Windows.Controls.ScrollViewer> denetiminin eşlerine nasıl aktarır şekilde gösterir.  
  
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
  
 Desen işleme için bir alt öğe belirtmek için, bu kod alt öğe <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> nesnesini <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> alır, yöntemi kullanarak bir eş oluşturur, yeni eşin özelliğini geçerli eşe ayarlar ve yeni eş döndürür. Bir <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> alt öğe üzerinde ayar, alt öğenin otomasyon eş ağacında görünmesini engeller ve alt öğe tarafından <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>yükseltilen tüm olayları ' da belirtilen denetimden kaynaklanan olarak belirtir. Denetim <xref:System.Windows.Controls.ScrollViewer> otomasyon ağacında görünmez ve oluşturduğu kaydırma olayları <xref:System.Windows.Controls.ItemsControl> nesneden kaynaklanıyor muş gibi görünür.  
  
### <a name="override-core-methods"></a>"Çekirdek" Yöntemlerini Geçersiz Kılın  
 Otomasyon kodu, eş sınıfının ortak yöntemlerini arayarak denetiminiz hakkında bilgi alır. Denetiminiz hakkında bilgi sağlamak için, denetim uygulamanız taban otomasyon eş sınıfı tarafından sağlanandan farklı olduğunda adı "Core" ile biten her yöntemi geçersiz kılın. En azından, denetiminiz aşağıdaki <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> örnekte gösterildiği gibi yöntemleri ve yöntemleri uygulamalıdır.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Uygulamanız, <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> bir <xref:System.Windows.Automation.ControlType> değer döndürerek denetiminizi açıklar. İade <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>edebilirsiniz rağmen, denetimdoğru açıklar eğer daha özel denetim türlerinden birini döndürmeniz gerekir. Döndürme <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> değeri sağlayıcının uygulaması [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]için fazladan [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] çalışma gerektirir ve istemci ürünleri denetim yapısını, klavye etkileşimini ve olası denetim desenlerini tahmin edemez.  
  
 <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> Denetiminizin <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> veri içeriği içerip içermediğini veya kullanıcı arabiriminde (veya her ikisinde) etkileşimli bir rolü yerine getirip getirmediğini belirtmek için yöntemleri uygulayın. Varsayılan olarak, her `true`iki yöntem de döndürün. Bu ayarlar, otomasyon ağacını filtrelemek için bu yöntemleri kullanabilecek olan ekran okuyucular gibi otomasyon araçlarının kullanılabilirliğini artırır. Yönteminiz <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> desen işlemeyi bir alt öğe eşine <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> aktarıyorsa, alt öğe eşin yöntemi alt öğe eşini otomasyon ağacından gizlemek için yanlış döndürebilir. Örneğin, <xref:System.Windows.Controls.ListBox> a kaydırma bir <xref:System.Windows.Controls.ScrollViewer>tarafından işlenir ve otomasyon <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> eş ile <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> ilişkili <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> yöntemi ile döndürülür <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Bu <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> nedenle, <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> döner `false`yöntemi , <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> böylece otomasyon ağacında görünmüyor.  
  
 Otomasyon eşin, denetiminiz için uygun varsayılan değerleri sağlamalıdır. Denetiminize başvuran XAML'nin öznitelikleri ekleyerek <xref:System.Windows.Automation.AutomationProperties> temel yöntemlerin eş uygulamalarınızı geçersiz kılabilir. Örneğin, aşağıdaki XAML iki özelleştirilmiş [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] özelliklere sahip bir düğme oluşturur.  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Desen Sağlayıcılarını Uygula  
 Özel bir sağlayıcı tarafından uygulanan arabirimler, sahip olan öğe doğrudan .'den <xref:System.Windows.Controls.Control>türemişse açıkça beyan edilir. Örneğin, aşağıdaki kod, aralık değeri <xref:System.Windows.Controls.Control> uygulayan bir eş bildirir.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Sahip denetimi, <xref:System.Windows.Controls.Primitives.RangeBase>eş eşdeğer türemiş bir eş sınıfından türetilebilir gibi belirli bir denetim türünden kaynaklanıyorsa. Bu durumda, eş türetilmiştir <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, hangi bir <xref:System.Windows.Automation.Provider.IRangeValueProvider>temel uygulama sağlar. Aşağıdaki kod, böyle bir eşin bildirimini gösterir.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Örnek bir uygulama için, Bir NumericUpDown özel denetimini uygulayan ve kullanan [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) veya [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) kaynak koduna bakın.  
  
### <a name="raise-events"></a>Etkinlikleri Yükseltin  
 Otomasyon istemcileri otomasyon etkinliklerine abone olabilir. Özel denetimler <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> yöntemi çağırarak denetim durumu değişiklikleri bildirmelidir. Benzer şekilde, bir özellik değeri <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> değiştiğinde, yöntemi çağırın. Aşağıdaki kod, eş nesnesinin denetim kodu içinden nasıl alınıp bir olayı yükseltmek için bir yöntem çağırılabildiğini gösterir. Bir optimizasyon olarak, kod bu olay türü için herhangi bir dinleyici olup olmadığını belirler. Olayı yalnızca dinleyiciler olduğunda yükseltmek gereksiz yükü önler ve denetimin yanıt vermesini sağlar.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](../../ui-automation/ui-automation-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [GitHub'da SayısalUpDown özel denetimi (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [GitHub'da SayısalUpDown özel kontrolü (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
