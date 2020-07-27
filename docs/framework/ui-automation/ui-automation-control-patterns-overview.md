---
title: UI Otomasyon Denetim Düzenlerine Genel Bakış
description: UI Otomasyonu Denetim desenlerine genel bakış konusuna bakın. Denetim desenleri, tür ya da görünüm ne olursa olsun bir denetimin işlevselliğini sınıflandırmasına ve kullanıma sunmanıza olanak tanır.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: d0df24de4f8a877405dfecb6b0d245ff1caf0418
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163888"
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakışta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim desenleri tanıtılmıştır. Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ortak denetim davranışlarını temsil etmek için denetim desenlerini kullanır. Örneğin, çağrılan denetimler (örneğin, düğmeler) ve kaydırma çubuklarına sahip denetimler (liste kutuları, liste görünümleri veya Birleşik giriş kutuları gibi) için kaydırma denetim deseninin çağrılması için Invoke denetim modelini kullanırsınız. Her denetim deseninin ayrı bir işlevi temsil ettiği için, belirli bir denetim tarafından desteklenen işlevlerin tamamını betimleyerek birleştirilebilecek.  
  
> [!NOTE]
> Üst öğe tarafından sunulan işlevleri sağlayan alt denetimler ile oluşturulan toplama denetimleri, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] normalde her bir alt denetimle ilişkili tüm denetim düzenlerini uygulamalıdır. Buna karşılık, aynı denetim desenlerinin alt denetimler tarafından uygulanması gerekmez.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyonu Denetim deseninin bileşenleri  
 Denetim desenleri, bir denetimde kullanılabilen ayrı bir işlev parçasını tanımlamak için gereken yöntemleri, özellikleri, olayları ve ilişkileri destekler.  
  
- UI Otomasyon öğesi ve onun üst öğesi arasındaki ilişki, alt ve eşdüzey öğeleri, öğenin ağaç içindeki yapısını açıklar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
- Yöntemler, Kullanıcı Arabirimi Otomasyonu istemcilerinin denetimi işlemesini sağlar.  
  
- Özellikler ve olaylar denetim deseninin işlevselliği ve denetimin durumu hakkında bilgi sağlar.  
  
 Denetim desenleri, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bileşen nesne modeli (com) nesneleriyle bağlantılı olarak arabirimler ile ilgilidir. COM ' da, hangi arabirimlerin desteklediğini sormak için bir nesneyi sorgulayabilir ve sonra bu arabirimleri işlevlerine erişmek için kullanabilirsiniz. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , UI Otomasyonu istemcileri, desteklenen denetim desenleri tarafından kullanıma sunulan özellikler, Yöntemler, olaylar ve yapılar aracılığıyla denetimle etkileşime geçmesini sağlayan bir denetim sorabilir. Örneğin, çok satırlı bir düzenleme kutusu için UI Otomasyon sağlayıcıları uygular <xref:System.Windows.Automation.Provider.IScrollProvider> . Bir istemci bir <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.ScrollPattern> Denetim modelini desteklediğinde, denetimi işlemek için bu denetim deseninin açığa çıkarılan özellikleri, yöntemleri ve olayları kullanabilir veya denetimle ilgili bilgilere erişebilirsiniz.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyon sağlayıcıları ve Istemcileri  
 UI Otomasyon sağlayıcıları, denetim tarafından desteklenen belirli bir işlev parçası için uygun davranışı açığa çıkarmak üzere Denetim desenleri uygular.  
  
 UI Otomasyonu istemcileri denetim deseninin yöntemlerine ve özelliklerine erişir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve bunları, veya ile ilgili bilgi almak için kullanır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Bu denetim deseninin sınıfları ad alanında bulunur <xref:System.Windows.Automation> (örneğin, <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.SelectionPattern> ).  
  
 İstemciler <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> , bir düzendeki özelliklere erişmek için yöntemleri (veya gibi) veya ortak dil çalışma zamanı (CLR) erişimcileri kullanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Her denetim deseninin sınıfı, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> Bu denetim modelini tanımlayan bir alan üyesine (veya veya <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType> ) sahiptir ve <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir için bu deseninin alınması veya bir parametre olarak geçirilebileceğini belirtir <xref:System.Windows.Automation.AutomationElement> .  
  
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
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Boyutlandırma ve belirtilen bir hücreye taşıma gibi kılavuz işlevlerini destekleyen denetimler için kullanılır. Örneğin, Windows Gezgini 'ndeki büyük simge görünümü veya Microsoft Word 'de üst bilgi içermeyen basit tablolar.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Kılavuzlar içinde hücreler bulunan denetimler için kullanılır. Tek tek hücreler GridItem modelini desteklemelidir. Örneğin, Microsoft Windows Explorer ayrıntı görünümündeki her bir hücre.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Düğme gibi çağrılabilecek denetimler için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Aynı bilgi, veri veya alt öğe kümesinin birden çok gösterimi arasında geçiş yapılabilir denetimler için kullanılır. Örneğin, verilerin küçük resim, kutucuk, simge, liste veya ayrıntı görünümlerinde kullanılabildiği bir liste görünümü denetimi.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Denetime uygulanabilen bir değer aralığına sahip denetimler için kullanılır. Örneğin, yıllar içeren bir değer değiştirici denetimi 2010 1900 aralığında olabilir, ancak ay sunan başka bir değer değiştirici denetimi 1 ile 12 arasında bir aralığa sahip olur.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabileceği denetimler için kullanılır. Örneğin, denetimin görüntülenebilir alanında görüntülenebileceğinden daha fazla bilgi olduğunda etkin olan kaydırma çubuklarına sahip bir denetim.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Kayan bir listedeki öğeleri tek tek içeren denetimler için kullanılır. Örneğin, bir Birleşik giriş kutusu denetimi gibi, kaydırma listesinde tek tek öğeleri olan bir liste denetimidir.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcısı denetimleri için kullanılır. Örneğin, liste kutuları ve Birleşik giriş kutuları.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Liste kutuları ve Birleşik giriş kutuları gibi seçim kapsayıcısı denetimlerindeki tek tek öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Kılavuza ve başlık bilgilerine sahip denetimler için kullanılır. Örneğin, Microsoft Excel çalışma sayfaları.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Tablodaki öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Düzenleme denetimleri ve metin bilgilerini açığa çıkaran belgeler için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Durumun değiştirilebilir olduğu denetimler için kullanılır. Örneğin, onay kutuları ve kullanıma ılabilir menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılabileceği, taşınabilecek ve döndürülebilen denetimler için kullanılır. Dönüşüm denetim deseninin tipik kullanımları tasarımcılar, formlar, grafik düzenleyiciler ve çizim uygulamalarıdır.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|İstemcilerin bir değer aralığını desteklemeyen denetimlerde değer almasına veya ayarlamasına izin verir. Örneğin, bir tarih saat seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Microsoft Windows işletim sistemi için temel bir kavram olan Windows 'a özgü bilgileri gösterir. Windows, en üst düzey uygulama pencereleri (Microsoft Word, Microsoft Windows Gezgini, vb.), birden çok belge arabirimi (MDI) alt pencereleri ve iletişim kutuları olan denetimlere örnektir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi](control-pattern-mapping-for-ui-automation-clients.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
- [İstemciler İçin UI Otomasyon Özellikleri](ui-automation-properties-for-clients.md)
- [İstemciler İçin UI Otomasyon Olayları](ui-automation-events-for-clients.md)
