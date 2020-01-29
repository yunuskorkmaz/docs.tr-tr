---
title: Özel denetim için UI Otomasyonu
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
ms.openlocfilehash: a370ed2c6b1f3273eca93b4865a032e8299f1cfb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738207"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF Özel Denetiminin UI Otomasyonu
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)], Otomasyon istemcilerinin çeşitli platformlar ve çerçeveler için kullanıcı arabirimlerini incelemek veya işletmek üzere kullanabileceği tek ve genelleştirilmiş bir arabirim sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], Kullanıcı arabirimi öğelerini incelemek ve diğer koddan kullanıcı etkileşiminin benzetimini yapmak için hem kalite güvencesi (test) kodu hem de ekran okuyucular gibi Erişilebilirlik uygulamalarının her ikisini de sağlar. Tüm platformlar genelinde [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] hakkında bilgi için bkz. erişilebilirlik.  
  
 Bu konuda, bir WPF uygulamasında çalışan özel bir denetim için sunucu tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağı açıklanmaktadır. WPF, Kullanıcı arabirimi öğelerinin ağacını paraleleden bir eşdüzey Otomasyon nesneleri ağacı aracılığıyla [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] destekler. Erişilebilirlik özellikleri sağlayan test kodu ve uygulamaları, doğrudan Otomasyon eşi nesneleri (işlem içi kod için) veya [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]tarafından sağlanmış Genelleştirilmiş arabirim aracılığıyla kullanabilir.  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Otomasyon eş sınıfları  
 WPF denetimleri, <xref:System.Windows.Automation.Peers.AutomationPeer>türeten bir eş sınıf ağacı aracılığıyla [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] destekler. Kurala göre, eş sınıf adları denetim sınıfı adıyla başlar ve "AutomationPeer" ile biter. Örneğin, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> <xref:System.Windows.Controls.Button> denetim sınıfının eşdüzey sınıfıdır. Eş sınıflar, [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerine kabaca eşdeğerdir, ancak WPF öğelerine özeldir. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] arabirimi aracılığıyla WPF uygulamalarına erişen Otomasyon kodu doğrudan otomasyon eşleri kullanmaz, ancak aynı işlem alanındaki Otomasyon kodu doğrudan Otomasyon eşlerini kullanabilir.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Yerleşik Otomasyon eşi sınıfları  
 Kullanıcılar, Kullanıcı tarafından arabirim etkinliğini kabul ederlerse veya ekran okuyucu uygulamaları kullanıcılarına gereken bilgileri içeriyorsa, bir Automation eşdüzey sınıfı uygular. Tüm WPF görsel öğelerinde otomasyon eşleri yoktur. Automation eşleri uygulayan sınıfların örnekleri <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>ve <xref:System.Windows.Controls.Label>. Automation eşleri uygulamayan sınıfların örnekleri, <xref:System.Windows.Controls.Border>gibi <xref:System.Windows.Controls.Decorator>ve <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.Canvas>gibi <xref:System.Windows.Controls.Panel>temel sınıflar gibi sınıflardır.  
  
 Temel <xref:System.Windows.Controls.Control> sınıfının karşılık gelen bir eşdüzey sınıfı yok. <xref:System.Windows.Controls.Control>türetilen özel bir denetime karşılık gelen bir eş sınıfa ihtiyacınız varsa, özel eşdüzey sınıfını <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>türetmelisiniz.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Türetilmiş Peers ilgili güvenlik konuları  
 Otomasyon eşleri kısmi güven ortamında çalıştırılmalıdır. UIAutomationClient derlemesinde bulunan kod, kısmi güven ortamında çalışacak şekilde yapılandırılmamış ve Otomasyon eş kodu bu derlemeye başvurmamalıdır. Bunun yerine, UIAutomationTypes derlemesinde sınıfları kullanmanız gerekir. Örneğin, UIAutomationClient derlemesinde <xref:System.Windows.Automation.AutomationElement> sınıfına karşılık gelen UIAutomationTypes derlemesinden <xref:System.Windows.Automation.AutomationElementIdentifiers> sınıfını kullanmanız gerekir. Automation eşdüzey kodundaki UIAutomationTypes derlemesine başvurmak güvenlidir.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Eş gezinti  
 Otomasyon eşi bulduktan sonra, işlem içi kod nesnenin <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> yöntemlerini çağırarak eşdüzey ağaca gidebilir. Bir denetim içindeki WPF öğeleri arasında gezinme, eşin <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> yönteminin uygulanması tarafından desteklenir. UI Otomasyon sistemi, denetimde bulunan alt öğeleri ağacı oluşturmak için bu yöntemi çağırır; Örneğin, liste kutusu içindeki öğeleri listeleyin. Varsayılan <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> yöntemi, Otomasyon eşlerinin ağacını oluşturmak için öğelerin görsel ağacını geçer. Özel denetimler, alt öğeleri otomasyon istemcilerine sunmak, bilgi ileten veya kullanıcı etkileşimine izin veren öğelerin Otomasyon eşlerini döndüren bu yöntemi geçersiz kılar.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Türetilmiş bir eş içindeki özelleştirmeler  
 <xref:System.Windows.UIElement> ve <xref:System.Windows.ContentElement> türetilen tüm sınıflar, korunan sanal yöntem <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>içerir. WPF, her denetim için Otomasyon eşi nesnesini almak üzere <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> çağırır. Otomasyon kodu, bir denetimin özellikleri ve özellikleri hakkında bilgi almak ve etkileşimli kullanım benzetimi yapmak için eşi kullanabilir. Otomasyonu destekleyen özel bir denetim <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> geçersiz kılmalıdır ve <xref:System.Windows.Automation.Peers.AutomationPeer>türetilen bir sınıfın örneğini döndürmelidir. Örneğin, özel bir denetim <xref:System.Windows.Controls.Primitives.ButtonBase> sınıfından türetiliyor, <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> tarafından döndürülen nesne <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>türetmelidir.  
  
 Özel bir denetim uygularken, temel Otomasyon eş sınıfından "Core" yöntemlerini geçersiz kılmanız gerekir ve özel denetimi özel denetimine özgü davranışı betimleyen.  
  
### <a name="override-oncreateautomationpeer"></a>OnCreateAutomationPeer öğesini geçersiz kıl  
 Özel denetiminizin <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> yöntemini, doğrudan veya dolaylı olarak <xref:System.Windows.Automation.Peers.AutomationPeer>türetmeniz gereken sağlayıcı nesnenizin döndürdüğü şekilde geçersiz kılın.  
  
### <a name="override-getpattern"></a>GetModel geçersiz kıl  
 Otomasyon eşleri, sunucu tarafı [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılarının bazı uygulama yönlerini basitleştirir, ancak özel denetim Otomasyonu eşleri yine de model arabirimlerini işlemelidir. WPF olmayan sağlayıcılar gibi, <xref:System.Windows.Automation.Provider.IInvokeProvider>gibi <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> ad alanındaki arabirimlerin uygulamalarını sağlayarak eşler denetim düzenlerini destekler. Denetim deseninin arabirimleri, eş ya da başka bir nesne tarafından uygulanabilir. Eşin <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> uygulanması, belirtilen kalıbı destekleyen nesneyi döndürür. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kod <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemini çağırır ve bir <xref:System.Windows.Automation.Peers.PatternInterface> numaralandırma değeri belirtir. <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> geçersiz kılma, belirtilen kalıbı uygulayan nesneyi döndürmelidir. Denetiminizin özel bir kalıp uygulamasına sahip olmaması durumunda, bu denetim türü için model desteklenmiyorsa, onun uygulamasını veya null değerini almak üzere <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> için temel türün uygulamasını çağırabilirsiniz. Örneğin, özel bir NumericUpDown denetimi bir Aralık içindeki değere ayarlanabilir, bu nedenle [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] eşi <xref:System.Windows.Automation.Provider.IRangeValueProvider> arabirimini uygular. Aşağıdaki örnek, bir <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> değerine yanıt vermek için eşin <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yönteminin nasıl geçersiz kılınacağını göstermektedir.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Bir <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> yöntemi, bir alt öğesi de bir kalıp sağlayıcı olarak belirtebilir. Aşağıdaki kod <xref:System.Windows.Controls.ItemsControl>, kaydırma deseninin işlemesini kendi iç <xref:System.Windows.Controls.ScrollViewer> denetiminin eşine nasıl aktardığından gösterir.  
  
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
  
 Bu kod, model işleme için bir alt öğesi belirtmek için, subelement nesnesini alır, <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> yöntemini kullanarak bir eş oluşturur, yeni eşin <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> özelliğini geçerli eşe ayarlar ve yeni eşi döndürür. Bir alt öğe üzerinde <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> ayarlanması, subelement öğesinin Otomasyon eş ağacında görünmesini önler ve alt öğesi tarafından oluşturulan tüm olayları <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>belirtilen denetimden kaynaklanan şekilde atar. <xref:System.Windows.Controls.ScrollViewer> denetimi Otomasyon ağacında görünmez ve oluşturduğu kayan olaylar <xref:System.Windows.Controls.ItemsControl> nesnesinden geliyor gibi görünür.  
  
### <a name="override-core-methods"></a>"Core" yöntemlerini geçersiz kıl  
 Otomasyon kodu, eş sınıfının ortak yöntemlerini çağırarak denetiminiz hakkında bilgi alır. Denetiminiz hakkında bilgi sağlamak için, denetim uygulamanız temel Otomasyon eş sınıfı tarafından sağlananlar dışında olduğunda, adı "çekirdek" ile biten her bir yöntemi geçersiz kılın. En azından, aşağıdaki örnekte gösterildiği gibi denetiminizin <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> yöntemlerini uygulaması gerekir.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> uygulamanız, <xref:System.Windows.Automation.ControlType> bir değer döndürerek denetiminizi açıklar. <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>döndürebilseniz de, denetiminizi doğru bir şekilde açıkladıysanız, daha belirli denetim türlerinden birini döndürmelisiniz. <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> dönüş değeri, sağlayıcının [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]uygulaması için ek iş gerektirir ve [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] istemci ürünleri denetim yapısını, klavye etkileşimini ve olası denetim düzenlerini tahmin edemiyor.  
  
 Denetiminizin veri içeriği içerip içermediğini veya Kullanıcı arabiriminde (veya her ikisi de) etkileşimli bir rolü yerine getirip gerçekleştirmediğini göstermek için <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> ve <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemlerini uygulayın. Varsayılan olarak, her iki yöntem de `true`döndürür. Bu ayarlar, Otomasyon ağacını filtrelemek için bu yöntemleri kullanan ekran okuyucular gibi otomasyon araçlarının kullanılabilirliğini geliştirir. <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> yöntemi bir alt öğe eşine model işleme aktardıysanız, alt öğe eşi <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi, Otomasyon ağacından alt öğe eşi gizlemek için false döndürebilir. Örneğin, bir <xref:System.Windows.Controls.ListBox> kaydırma <xref:System.Windows.Controls.ScrollViewer>tarafından işlenir ve <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> Otomasyon eşi, <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> ilişkili <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer><xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> yöntemi tarafından döndürülür. Bu nedenle, <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> yöntemi `false`döndürür, böylece <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> Otomasyon ağacında görünmez.  
  
 Otomasyon eşlerinizin, denetiminiz için uygun varsayılan değerleri sağlaması gerekir. Denetime başvuran XAML, <xref:System.Windows.Automation.AutomationProperties> öznitelikleri ekleyerek temel yöntemlerin eş uygulamalarınızı geçersiz kılabileceğini unutmayın. Örneğin, aşağıdaki XAML iki özelleştirilmiş [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] özelliği olan bir düğme oluşturur.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Model sağlayıcıları uygulama  
 Özel bir sağlayıcı tarafından uygulanan arabirimler, sahip olan öğe doğrudan <xref:System.Windows.Controls.Control>türettiği takdirde açıkça bildirilmiştir. Örneğin, aşağıdaki kod bir Aralık değeri uygulayan <xref:System.Windows.Controls.Control> için bir eş bildirir.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Sahip olan denetim <xref:System.Windows.Controls.Primitives.RangeBase>gibi belirli bir denetim türünden türetildiyse, eş bir eşdeğer türetilmiş eş sınıfından türetilebilir. Bu durumda, eş <xref:System.Windows.Automation.Provider.IRangeValueProvider>temel bir uygulama sağlayan <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>türetilir. Aşağıdaki kod bu tür bir eşin bildirimini gösterir.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Örnek bir uygulama için, bir NumericUpDown [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) özel denetimi uygulayan veya [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) kaynak koduna bakın.  
  
### <a name="raise-events"></a>Olay oluştur  
 Otomasyon istemcileri Otomasyon olaylarına abone olabilir. Özel denetimler <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> yöntemini çağırarak Denetim durumundaki değişiklikleri rapormalıdır. Benzer şekilde, bir özellik değeri değiştiğinde <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> yöntemini çağırın. Aşağıdaki kod, içindeki eşdüzey nesnenin denetim kodunun içinden nasıl alınacağını ve bir olay tetikleyebilme yöntemi nasıl çağrılacağını gösterir. Bir iyileştirme olarak, kod bu olay türü için herhangi bir dinleyici olup olmadığını belirler. Olayı yalnızca dinleyiciler olduğunda, gereksiz ek yükü önlediği ve denetimin yanıt vermeye devam etmesine yardımcı olur.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonuna Genel Bakış](../../ui-automation/ui-automation-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [GitHub 'da NumericUpDown özelC#denetimi ()](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [GitHub 'da NumericUpDown özel denetimi (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
