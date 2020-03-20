---
title: UI Otomasyon Denetim Düzenlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: f62631a15dd348b6f6ea27a82d7b45aab92ceed2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179944"
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bakış denetim desenleri sunar. Denetim desenleri, denetim türünden veya denetimin görünümünden bağımsız olarak bir denetimin işlevselliğini kategorilere ayırmak ve ortaya çıkarmak için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ortak denetim davranışlarını temsil etmek için denetim desenleri kullanır. Örneğin, çağrılabilen denetimler (düğmeler gibi) için Invoke denetim deseni ve kaydırma çubukları (liste kutuları, liste görünümleri veya açılan kutular gibi) denetimler için Kaydırma denetim deseni kullanırsınız. Her denetim deseni ayrı bir işlevselliği temsil ettiği için, belirli bir denetim tarafından desteklenen tam işlevsellik kümesini açıklamak için birleştirilebilirler.  
  
> [!NOTE]
> Üst öğenin [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] maruz kaçtığı işlevselliği sağlayan alt denetimlerle oluşturulmuş toplu denetimler, normalde her alt denetimle ilişkili tüm denetim modellerini uygulamalıdır. Buna karşılık, aynı kontrol desenleri alt denetimleri tarafından uygulanması gerekmez.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyon Kontrol Desen Bileşenleri  
 Denetim desenleri, denetimde kullanılabilen ayrı bir işlevsellik parçasını tanımlamak için gereken yöntemleri, özellikleri, olayları ve ilişkileri destekler.  
  
- Bir UI Automation öğesi ile üst öğesi, alt ve kardeşleri arasındaki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilişki, öğenin ağaç içindeki yapısını açıklar.  
  
- Yöntemler, UI Automation istemcilerinin denetimi işlemesine olanak sağlar.  
  
- Özellikler ve olaylar, denetim deseninin işlevselliği ve denetimin durumu hakkında bilgi sağlar.  
  
 Denetim desenleri, arabirimler Bileşen Nesne Modeli (COM) nesneleri ile ilişkili [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olarak ilgilidir. COM'da, hangi arabirimleri desteklediğini sormak için bir nesneyi sorgulayabilir ve işlevsellik erişmek için bu arabirimleri kullanabilirsiniz. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], UI Automation istemcileri desteklediği desenleri kontrol eden bir denetim isteyebilir ve desteklenen denetim desenleri tarafından maruz kalan özellikler, yöntemler, olaylar ve yapılar aracılığıyla denetimle etkileşime geçebilir. Örneğin, çok satırlı bir düzen kutusu için, <xref:System.Windows.Automation.Provider.IScrollProvider>UI Otomasyon sağlayıcıları uygular. İstemci denetim <xref:System.Windows.Automation.AutomationElement> deseni <xref:System.Windows.Automation.ScrollPattern> desteklediğini biliyorsa, denetimi işlemek veya denetimle ilgili bilgilere erişmek için bu denetim deseni tarafından maruz kalan özellikleri, yöntemleri ve olayları kullanabilir.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyon Sağlayıcıları ve Müşterileri  
 UI Otomasyon sağlayıcıları, denetim tarafından desteklenen belirli bir işlevsellik parçası için uygun davranışı ortaya çıkarmak için denetim desenleri uygular.  
  
 UI Automation istemcileri kontrol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] deseni sınıflarının yöntemlerine ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]özelliklerine erişerek, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]bu sınıfları , Bu denetim deseni sınıfları <xref:System.Windows.Automation> ad alanında <xref:System.Windows.Automation.InvokePattern> bulunur <xref:System.Windows.Automation.SelectionPattern>(örneğin, ve).  
  
 İstemciler, desendeki <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklere erişmek için yöntemleri (örneğin <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> veya) veya ortak dil çalışma zamanı (CLR) erişimcileri kullanır. Her denetim deseni sınıfının bir <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> alan <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>üyesi (örneğin, veya) bu denetim deseni <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> tanımlayan bir alan <xref:System.Windows.Automation.AutomationElement>üyesi vardır <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ve bir .  
  
<a name="uiautomation_control_patterns_dynamic"></a>
## <a name="dynamic-control-patterns"></a>Dinamik Kontrol Desenleri  
 Bazı denetimler her zaman aynı denetim desen kümesini desteklemez. Denetim desenleri, bir UI Automation istemcisi tarafından kullanılabilir olduğunda desteklenmiş olarak kabul edilir. Örneğin, çok satırlı bir düzen kutusu dikey kaydırmayı yalnızca görüntülenebilir alanında görüntülenenden daha fazla metin satırı içerdiğinde etkinleştirirken. Kaydırma, kaydırmanın artık gerekmemesi için yeterli metin kaldırıldığında devre dışı bırakılır. Bu örnekte, ScrollPattern denetim deseni denetimin geçerli durumuna (düzen kutusunda ne kadar metin olduğuna) bağlı olarak dinamik olarak desteklenir.  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>
## <a name="control-pattern-classes-and-interfaces"></a>Denetim Desen Sınıfları ve Arayüzleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri açıklanmaktadır. Tablo ayrıca, denetim desenleri erişmek için UI Automation istemcileri tarafından kullanılan sınıfları ve bunları uygulamak için UI Automation sağlayıcıları tarafından kullanılan arabirimleri listeler.  
  
|Kontrol Deseni Sınıfı|Sağlayıcı Arabirimi|Açıklama|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Bir yerleştirme kabına kenetlenebilecek denetimler için kullanılır. Örneğin, araç çubukları veya takım paletleri.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Genişletilebilen veya daraltılmış denetimler için kullanılır. Örneğin, **Dosya** menüsü gibi bir uygulamadaki menü öğeleri.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Boyutlandırma ve belirli bir hücreye taşıma gibi ızgara işlevselliğini destekleyen denetimler için kullanılır. Örneğin, Windows Gezgini'ndeki büyük simge görünümü veya Microsoft Word'de üstbilgi içermeyen basit tablolar.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Izgaralar içinde hücreleri olan denetimler için kullanılır. Tek tek hücreler GridItem deseni desteklemelidir. Örneğin, Microsoft Windows Gezgini'ndeki her hücre ayrıntı görünümünde.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Düğme gibi çağrılabilen denetimler için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Aynı bilgi, veri veya alt kümesinin birden çok gösterimi arasında geçiş yapabilecek denetimler için kullanılır. Örneğin, küçük resim, döşeme, simge, liste veya ayrıntı görünümlerinde verilerin bulunduğu bir liste görünümü denetimi.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Denetime uygulanabilecek bir değer aralığına sahip denetimler için kullanılır. Örneğin, yıl içeren bir spinner denetimi 1900 ile 2010 arasında bir aralara sahip olabilirken, sunan başka bir spinner denetimi 1 ile 12 arasında bir aralara sahip olabilir.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabilen denetimler için kullanılır. Örneğin, denetimin görüntülenebilir alanında görüntülenebilenden daha fazla bilgi olduğunda etkin olan kaydırma çubukları olan bir denetim.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Kaydıran bir listede tek tek öğeleri olan denetimler için kullanılır. Örneğin, kaydırma listesinde açılan kutu denetimi gibi tek tek öğeleri olan bir liste denetimi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcı denetimleri için kullanılır. Örneğin, liste kutuları ve açılan kutular.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Liste kutuları ve açılan kutular gibi seçim kapsayıcı sıyrık denetimlerinde tek tek öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Üstbilgi bilgilerinin yanı sıra ızgaraya sahip denetimler için kullanılır. Örneğin, Microsoft Excel çalışma sayfaları.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Tablodaki öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Metin bilgilerini ortaya çıkaran denetimleri ve belgeleri düzenlenmesi için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Durum değiştirilebilen denetimler için kullanılır. Örneğin, onay kutuları ve onaylanabilir menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılabilen, taşınabilen ve döndürülebilen denetimler için kullanılır. Dönüşüm denetim deseni için tipik kullanımlar tasarımcılarda, formlarda, grafik düzenleyicilerde ve çizim uygulamalarındadır.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|İstemcilerin çeşitli değerleri desteklemeyen denetimler üzerinde değer elde etmesine veya ayarlamasına olanak tanır. Örneğin, bir tarih saati seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Microsoft Windows işletim sistemine özgü temel bir kavram olan windows'a özgü bilgileri ortaya çıkarır. Windows denetimlerine örnek olarak üst düzey uygulama pencereleri (Microsoft Word, Microsoft Windows Explorer vb.), çoklu belge arabirimi (MDI) alt pencereler ve iletişim pencereleri verilebilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi](control-pattern-mapping-for-ui-automation-clients.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
