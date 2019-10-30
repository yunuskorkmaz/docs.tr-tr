---
title: UI Otomasyon Denetim Düzenlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: 548828f8e9948e000a15fd19a4475ef715e110d8
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039459"
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim desenleri tanıtılmıştır. Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ortak denetim davranışlarını temsil etmek için denetim desenlerini kullanır. Örneğin, çağrılan denetimler (örneğin, düğmeler) ve kaydırma çubuklarına sahip denetimler (liste kutuları, liste görünümleri veya Birleşik giriş kutuları gibi) için kaydırma denetim deseninin çağrılması için Invoke denetim modelini kullanırsınız. Her denetim deseninin ayrı bir işlevi temsil ettiği için, belirli bir denetim tarafından desteklenen işlevlerin tamamını betimleyerek birleştirilebilecek.  
  
> [!NOTE]
> Üst öğe tarafından sunulan işlevsellik için [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] sağlayan alt denetimler ile oluşturulan toplama denetimleri — normalde her bir alt denetimle ilişkili tüm denetim düzenlerini uygulamalıdır. Buna karşılık, aynı denetim desenlerinin alt denetimler tarafından uygulanması gerekmez.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyonu Denetim deseninin bileşenleri  
 Denetim desenleri, bir denetimde kullanılabilen ayrı bir işlev parçasını tanımlamak için gereken yöntemleri, özellikleri, olayları ve ilişkileri destekler.  
  
- UI Otomasyonu öğesi ve onun üst öğesi arasındaki ilişki, alt ve eşdüzey öğe [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı içinde öğenin yapısını açıklar.  
  
- Yöntemler, Kullanıcı Arabirimi Otomasyonu istemcilerinin denetimi işlemesini sağlar.  
  
- Özellikler ve olaylar denetim deseninin işlevselliği ve denetimin durumu hakkında bilgi sağlar.  
  
 Denetim desenleri, bileşen nesne modeli (COM) nesneleriyle bağlantılı arabirimler olarak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ile ilgilidir. COM ' da, hangi arabirimlerin desteklediğini sormak için bir nesneyi sorgulayabilir ve sonra bu arabirimleri işlevlerine erişmek için kullanabilirsiniz. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], UI Otomasyonu istemcileri, desteklediği desenleri, yöntemleri, olayları ve desteklenen denetim desenleri tarafından kullanıma sunulan yapılar aracılığıyla denetim ile etkileşime geçerek denetim için denetim kurabilir. Örneğin, çok satırlı bir düzenleme kutusu için UI Otomasyon sağlayıcıları <xref:System.Windows.Automation.Provider.IScrollProvider>uygular. Bir istemci bir <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.ScrollPattern> denetim modelini desteklediğini bildiği zaman, denetimi işlemek için bu denetim deseninin açığa çıkarılan özellikleri, yöntemleri ve olayları kullanabilir ya da denetimle ilgili bilgilere erişim sağlayabilir.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyon sağlayıcıları ve Istemcileri  
 UI Otomasyon sağlayıcıları, denetim tarafından desteklenen belirli bir işlev parçası için uygun davranışı açığa çıkarmak üzere Denetim desenleri uygular.  
  
 UI Otomasyonu istemcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim model sınıflarının yöntemlerine ve özelliklerine erişir ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]hakkında bilgi almak veya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]denetlemek için bunları kullanır. Bu denetim deseninin sınıfları <xref:System.Windows.Automation> ad alanında bulunur (örneğin, <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.SelectionPattern>).  
  
 İstemciler, bir düzendeki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerine erişmek için <xref:System.Windows.Automation.AutomationElement> Yöntemler (<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>gibi) veya ortak dil çalışma zamanı (CLR) erişimcileri kullanır. Her denetim deseninin, bu denetim modelini tanımlayan bir alan üyesi (örneğin, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> veya <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>) vardır ve bu kalıbı bir <xref:System.Windows.Automation.AutomationElement>almak için <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir parametre olarak geçirilebilir.  
  
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
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Boyutlandırma ve belirtilen bir hücreye taşıma gibi kılavuz işlevlerini destekleyen denetimler için kullanılır. Örneğin, Windows Gezgini 'ndeki büyük simge görünümü veya [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]üst bilgileri olmayan basit tablolar.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Kılavuzlar içinde hücreler bulunan denetimler için kullanılır. Tek tek hücreler GridItem modelini desteklemelidir. Örneğin, [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] ayrıntı görünümündeki her bir hücre.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Düğme gibi çağrılabilecek denetimler için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Aynı bilgi, veri veya alt öğe kümesinin birden çok gösterimi arasında geçiş yapılabilir denetimler için kullanılır. Örneğin, verilerin küçük resim, kutucuk, simge, liste veya ayrıntı görünümlerinde kullanılabildiği bir liste görünümü denetimi.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Denetime uygulanabilen bir değer aralığına sahip denetimler için kullanılır. Örneğin, yıllar içeren bir değer değiştirici denetimi 2010 1900 aralığında olabilir, ancak ay sunan başka bir değer değiştirici denetimi 1 ile 12 arasında bir aralığa sahip olur.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabileceği denetimler için kullanılır. Örneğin, denetimin görüntülenebilir alanında görüntülenebileceğinden daha fazla bilgi olduğunda etkin olan kaydırma çubuklarına sahip bir denetim.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Kayan bir listedeki öğeleri tek tek içeren denetimler için kullanılır. Örneğin, bir Birleşik giriş kutusu denetimi gibi, kaydırma listesinde tek tek öğeleri olan bir liste denetimidir.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcısı denetimleri için kullanılır. Örneğin, liste kutuları ve Birleşik giriş kutuları.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Liste kutuları ve Birleşik giriş kutuları gibi seçim kapsayıcısı denetimlerindeki tek tek öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Kılavuza ve başlık bilgilerine sahip denetimler için kullanılır. Örneğin, çalışma sayfalarını [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)].|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Tablodaki öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Düzenleme denetimleri ve metin bilgilerini açığa çıkaran belgeler için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Durumun değiştirilebilir olduğu denetimler için kullanılır. Örneğin, onay kutuları ve kullanıma ılabilir menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılabileceği, taşınabilecek ve döndürülebilen denetimler için kullanılır. Dönüşüm denetim deseninin tipik kullanımları tasarımcılar, formlar, grafik düzenleyiciler ve çizim uygulamalarıdır.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|İstemcilerin bir değer aralığını desteklemeyen denetimlerde değer almasına veya ayarlamasına izin verir. Örneğin, bir tarih saat seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Microsoft Windows işletim sistemi için temel bir kavram olan Windows 'a özgü bilgileri gösterir. Windows, en üst düzey uygulama pencereleri ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], vb.), birden çok belgeli arabirim (MDI) alt pencereleri ve iletişim kutuları olan denetimlere örnektir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](control-pattern-mapping-for-ui-automation-clients.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
