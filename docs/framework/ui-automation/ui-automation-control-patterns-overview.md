---
title: UI Otomasyon Denetim Düzenlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: 7587c8cd24197252506967208869bd454b4f27f2
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400677"
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim desenleri tanıtılmıştır. Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ortak denetim davranışlarını temsil etmek için denetim desenlerini kullanır. Örneğin, çağrılan denetimler (örneğin, düğmeler) ve kaydırma çubuklarına sahip denetimler (liste kutuları, liste görünümleri veya Birleşik giriş kutuları gibi) için kaydırma denetim deseninin çağrılması için Invoke denetim modelini kullanırsınız. Her denetim deseninin ayrı bir işlevi temsil ettiği için, belirli bir denetim tarafından desteklenen işlevlerin tamamını betimleyerek birleştirilebilecek.  
  
> [!NOTE]
>  Üst öğe tarafından sunulan işlevleri sağlayan alt denetimler ile oluşturulan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] toplama denetimleri, normalde her bir alt denetimle ilişkili tüm denetim düzenlerini uygulamalıdır. Buna karşılık, aynı denetim desenlerinin alt denetimler tarafından uygulanması gerekmez.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyonu Denetim deseninin bileşenleri  
 Denetim desenleri, bir denetimde kullanılabilen ayrı bir işlev parçasını tanımlamak için gereken yöntemleri, özellikleri, olayları ve ilişkileri destekler.  
  
- UI Otomasyon öğesi ve onun üst öğesi arasındaki ilişki, alt ve eşdüzey öğeleri, öğenin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç içindeki yapısını açıklar.  
  
- Yöntemler, Kullanıcı Arabirimi Otomasyonu istemcilerinin denetimi işlemesini sağlar.  
  
- Özellikler ve olaylar denetim deseninin işlevselliği ve denetimin durumu hakkında bilgi sağlar.  
  
 Denetim desenleri, [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] nesnelerle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bağlantılı arabirimler gibi ile ilgilidir. İçinde [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], hangi arabirimlerin desteklediğini sormak için bir nesneyi sorgulayabilir ve sonra bu arabirimleri işlevlerine erişmek için kullanabilirsiniz. ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, UI Otomasyonu istemcileri, desteklenen denetim desenleri tarafından kullanıma sunulan özellikler, Yöntemler, olaylar ve yapılar aracılığıyla denetimle etkileşime geçmesini sağlayan bir denetim sorabilir. Örneğin, çok satırlı bir düzenleme kutusu için UI Otomasyon sağlayıcıları uygular <xref:System.Windows.Automation.Provider.IScrollProvider>. Bir istemci bir <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.ScrollPattern> denetim modelini desteklediğinde, denetimi işlemek için bu denetim deseninin açığa çıkarılan özellikleri, yöntemleri ve olayları kullanabilir veya denetimle ilgili bilgilere erişebilirsiniz.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyon sağlayıcıları ve Istemcileri  
 UI Otomasyon sağlayıcıları, denetim tarafından desteklenen belirli bir işlev parçası için uygun davranışı açığa çıkarmak üzere Denetim desenleri uygular.  
  
 UI Otomasyonu istemcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim deseninin yöntemlerine ve özelliklerine erişir ve bunları, veya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ile [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ilgili bilgi almak için kullanır. Bu denetim deseninin sınıfları <xref:System.Windows.Automation> ad alanında bulunur (örneğin, <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.SelectionPattern>).  
  
 İstemciler, <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>bir düzendekiözelliklereerişmekiçinyöntemleri(veyagibi)veyaortakdilçalışmazamanı(CLR)erişimcilerikullanır.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Her denetim deseninin sınıfı, bu denetim modelini tanımlayan bir alan üyesine <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> ( <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>veya veya) sahiptir ve bir <xref:System.Windows.Automation.AutomationElement>için bu deseninin alınması <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir parametre olarak geçirilebileceğini belirtir.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Dinamik denetim desenleri  
 Bazı denetimler her zaman aynı denetim desenleri kümesini desteklemez. Denetim desenleri, bir UI Otomasyon istemcisi tarafından kullanılabilir olduğunda desteklenirler. Örneğin, çok satırlı bir düzenleme kutusu, yalnızca görüntülenebilir alanında görüntülenebileceğinden daha fazla satır metin içerdiğinde dikey kaydırmaya izin vermez. Kaydırmanın artık gerekli olmaması için yeterli metin kaldırıldığında kaydırma devre dışı bırakılır. Bu örnek için, Scrollmodel denetim deseninin, denetimin geçerli durumuna (düzenleme kutusunda ne kadar metin olduğunu) bağlı olarak dinamik olarak desteklendiği açıklanır.  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Denetim model sınıfları ve arabirimleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri açıklanmaktadır. Tablo ayrıca, Kullanıcı Arabirimi Otomasyonu istemcilerinin denetim desenlerine erişmek için kullandığı sınıfları ve UI Otomasyon sağlayıcılarının bunları uygulamak için kullandığı arabirimleri listeler.  
  
|Denetim deseninin sınıfı|Sağlayıcı arabirimi|Açıklama|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Bir yerleştirme kapsayıcısına sabitlenebilir denetimler için kullanılır. Örneğin, araç çubukları veya araç paletleri.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Genişletilebilecek veya daraltılabilen denetimler için kullanılır. Örneğin, **Dosya** menüsü gibi bir uygulamadaki menü öğeleri.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Boyutlandırma ve belirtilen bir hücreye taşıma gibi kılavuz işlevlerini destekleyen denetimler için kullanılır. Örneğin, Windows Gezgini 'ndeki büyük simge görünümü veya üst bilgisi [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]olmayan basit tablolar.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Kılavuzlar içinde hücreler bulunan denetimler için kullanılır. Tek tek hücreler GridItem modelini desteklemelidir. Örneğin, [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] ayrıntı görünümündeki her bir hücre.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Düğme gibi çağrılabilecek denetimler için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Aynı bilgi, veri veya alt öğe kümesinin birden çok gösterimi arasında geçiş yapılabilir denetimler için kullanılır. Örneğin, verilerin küçük resim, kutucuk, simge, liste veya ayrıntı görünümlerinde kullanılabildiği bir liste görünümü denetimi.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Denetime uygulanabilen bir değer aralığına sahip denetimler için kullanılır. Örneğin, yıllar içeren bir değer değiştirici denetimi 2010 1900 aralığında olabilir, ancak ay sunan başka bir değer değiştirici denetimi 1 ile 12 arasında bir aralığa sahip olur.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabileceği denetimler için kullanılır. Örneğin, denetimin görüntülenebilir alanında görüntülenebileceğinden daha fazla bilgi olduğunda etkin olan kaydırma çubuklarına sahip bir denetim.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Kayan bir listedeki öğeleri tek tek içeren denetimler için kullanılır. Örneğin, bir Birleşik giriş kutusu denetimi gibi, kaydırma listesinde tek tek öğeleri olan bir liste denetimidir.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcısı denetimleri için kullanılır. Örneğin, liste kutuları ve Birleşik giriş kutuları.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Liste kutuları ve Birleşik giriş kutuları gibi seçim kapsayıcısı denetimlerindeki tek tek öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Kılavuza ve başlık bilgilerine sahip denetimler için kullanılır. Örneğin, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] çalışma sayfaları.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Tablodaki öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Düzenleme denetimleri ve metin bilgilerini açığa çıkaran belgeler için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Durumun değiştirilebilir olduğu denetimler için kullanılır. Örneğin, onay kutuları ve kullanıma ılabilir menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılabileceği, taşınabilecek ve döndürülebilen denetimler için kullanılır. Dönüşüm denetim deseninin tipik kullanımları tasarımcılar, formlar, grafik düzenleyiciler ve çizim uygulamalarıdır.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|İstemcilerin bir değer aralığını desteklemeyen denetimlerde değer almasına veya ayarlamasına izin verir. Örneğin, bir tarih saat seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|[!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] İşletim sistemine yönelik temel bir kavram olan Windows 'a özgü bilgileri gösterir. Windows olan denetimlerin örnekleri, en üst düzey uygulama pencereleri ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], vb.), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt pencereler ve iletişim kutuları.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
