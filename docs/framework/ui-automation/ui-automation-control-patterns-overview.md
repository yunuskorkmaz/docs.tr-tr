---
title: "UI Otomasyon Denetim Düzenlerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
caps.latest.revision: "34"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e675681d1de3aa46645047da61ae8aac2ea0ba31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış sunar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim düzenleri. Denetim desenleri kategorilere ayırmak ve Denetim türü veya denetiminin görünümünü bağımsız bir denetimin işlevselliği kullanıma sunmak için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ortak denetim davranışları temsil etmek için düzenleri kullanır denetler. Örneğin, (düğme gibi) çağrılabilir denetimleri ve kaydırma çubukları (örneğin, liste kutuları, liste görünümleri veya birleşik giriş kutuları) sahip denetimleri için kaydırma denetim düzeni için Çağır denetim düzeni kullanın. Her denetim düzeni ayrı bir işlevi temsil ettiğinden belirli bir denetim tarafından desteklenen işlevleri kümesini tanımlamak için birleştirilebilir.  
  
> [!NOTE]
>  Denetimleri bir araya — sağlamak alt denetimleri ile oluşturulmuş [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] üst tarafından kullanıma sunulan işlevsellikten için — normalde her alt denetimi ile ilişkilendirilmiş tüm denetim düzenleri uygulamalıdır. Buna karşılık, bu aynı denetim düzenleri alt denetimlerin uygulanması için gerekli değildir.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyon denetim düzeni bileşenleri  
 Denetim desenleri yöntemler, özellikler, olaylar ve ayrık bir işlevi bir denetimde kullanılabilir tanımlamak için gerekli ilişkileri destekler.  
  
-   UI Otomasyon öğesi ve kendi üst, alt ve eşdüzey arasındaki ilişkiyi öğenin yapısında açıklayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.  
  
-   Denetim işlemek UI Otomasyon istemcileri yöntemler sağlar.  
  
-   Özellikleri ve olayları denetim deseninin işlevselliği hakkında bilgi ve aynı zamanda denetim durumu hakkında bilgi sağlar.  
  
 Denetim desenleri ilişkilendirmek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] arabirimleri ile ilgili olarak [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] nesneleri. İçinde [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], hangi arabirimlerin isteyin ve sonra bu arabirimlerine erişim işlevselliği kullanmak için bir nesne sorgulayabilirsiniz. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], UI Otomasyon istemcileri isteğe bağlı olarak hangi denetim destekler düzenleri denetim isteyin ve sonra denetimi özellikleri, yöntemleri, olayları ve desteklenen denetim düzenleri tarafından kullanıma sunulan yapıları aracılığıyla etkileşim. Örneğin, çok satırlı düzenleme kutusu için UI Otomasyon sağlayıcılar uygulamak <xref:System.Windows.Automation.Provider.IScrollProvider>. Ne zaman bir istemci bilir, bir <xref:System.Windows.Automation.AutomationElement> destekleyen <xref:System.Windows.Automation.ScrollPattern> denetim düzeni, özellikleri, yöntemleri ve olayları bu denetim düzeni tarafından kullanıma sunulan denetimi yönetmek veya denetimi hakkındaki bilgilere erişmek için kullanabilirsiniz.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyon sağlayıcılar ve istemciler  
 UI Otomasyon sağlayıcıları Denetim tarafından desteklenen işlevleri belirli bir parçası için uygun davranışı kullanıma sunmak için Denetim desenleri uygulayın.  
  
 UI Otomasyon istemcileri erişim yöntemleri ve özellikleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzeni sınıfları ve bunları hakkında bilgi almak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], veya işlemek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Bu denetim düzeni sınıfları bulunan <xref:System.Windows.Automation> ad alanı (örneğin, <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.SelectionPattern>).  
  
 İstemcilerin kullandığı <xref:System.Windows.Automation.AutomationElement> yöntemleri (gibi <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) veya [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] erişmek için erişimcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir desen özellikleri. Her denetim düzeni sınıfı bir alan üye var (örneğin, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType>'' veya <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), bu denetim düzeni tanımlar ve bir parametre olarak geçirilen <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> için bu deseni almak için bir <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Dinamik Denetim desenleri  
 Bazı denetimler her zaman aynı kümesini denetim düzenleri desteği yoktur. Denetim desenleri UI Otomasyonu istemciye kullanılabilir olduğunda desteklenen olarak kabul edilir. Örneğin, çok satırlı kutusunu etkinleştirir yalnızca metin görüntülenebilir alanında görüntülenebilenden daha fazla satırı içerdiğinde kaydırma dikey düzenleyin. Böylece kaydırma artık gerekli değildir yeterince metin kaldırıldığında kaydırmayı devre dışı bırakılır. Bu örnekte, ScrollPattern'ı denetim düzeni geçerli durumunu (ne kadar metin düzenleme kutusu içinde) denetimin bağlı olarak dinamik olarak desteklenir.  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Denetim düzeni sınıfları ve arabirimleri  
 Aşağıdaki tabloda açıklanmaktadır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri. Tabloda ayrıca bunları uygulama UI Otomasyon sağlayıcıları tarafından kullanılan arabirimlere yanı sıra denetim düzenleri erişmek için UI Otomasyon istemcileri tarafından kullanılan sınıflar listelenmektedir.  
  
|Denetim düzeni sınıfı|Sağlayıcı arabirimi|Açıklama|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Yerleşik bir kapsayıcıda yerleşik denetimleri için kullanılır. Örneğin, araç çubukları veya aracı paletleri.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Genişletilmiş veya daraltılmış denetimleri için kullanılır. Örneğin, menü bir uygulamada gibi öğeleri **dosya** menüsü.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Boyutlandırma ve belirtilen bir hücreye taşıma gibi kılavuz işlevlerini destekleyen denetimleri için kullanılır. Örneğin, büyük simge görüntülemek Windows Gezgini'nde veya üstbilgilerinde olmadan basit tablolar [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Kılavuzları hücrelerde denetimleri için kullanılır. Tek tek hücrelere GridItem düzeni desteklemelidir. Örneğin, her hücrede [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] ayrıntı görünümü.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Gibi bir düğme çağrılabilir denetimleri için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Birden çok gösterimlerini aynı bilgileri, veri veya alt kümesi arasında geçiş yapabilirsiniz denetimleri için kullanılır. Örneğin, bir liste görünümü denetimi veri küçük resim, döşeme, simge, liste veya Ayrıntılı Görünüm kullanılabilir olduğu.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bir denetime uygulanabilir değerleri aralığına sahip denetimleri için kullanılır. Örneğin, bir aralığı 1-12 ay sunan başka bir değer değiştirici denetim sahip olurken yıl içeren bir değer değiştirici denetim 1900 2010 'un, bir dizi olabilir.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabilirsiniz denetimleri için kullanılır. Örneğin, bir denetim denetimi görüntülenebilir alanında görüntülenebilenden daha fazla bilgi olduğunda etkin olan kaydırma çubukları sahip.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Kayan bir listede tek tek öğeleriniz denetimleri için kullanılır. Örneğin, kaydırma listesinde, bir birleşik giriş kutusu denetimi gibi ayrı öğeleri içeren bir liste denetimi.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcı denetimleri için kullanılır. Örneğin, liste kutuları ve birleşik giriş kutuları.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Liste kutuları ve birleşik giriş kutuları gibi seçim kapsayıcı denetimleri tek tek öğe için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Kılavuz denetimleri için kullanılan üstbilgi bilgilerinin yanı sıra. Örneğin, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] çalışma sayfaları.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Bir tablodaki öğeler için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Düzenleme denetimleri ve metin bilgilerini kullanıma belgeleri için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Durumunu burada değiştirilebilir denetimleri için kullanılır. Örneğin, onay kutularını ve checkable menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılabilir, taşınabilir, döndürülmüş ve yönetilebilen denetimleri için kullanılır. Dönüşüm denetim düzeni için tipik kullanım tasarımcıları, formlar, grafik düzenleyicilerden ve çizim uygulamaları şeklindedir.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Almak veya değerleri aralığı desteklemeyen denetimleri bir değer ayarlamak istemcilerin sağlar. Örneğin, bir tarih saat Seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Windows, için'ın temel kavramlarından özgü bilgiler sunan [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] işletim sistemi. Windows denetimleri örnekler en üst düzey uygulama windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], vb.), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt öğe pencerelerini ve iletişim kutuları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [İstemciler İçin UI Otomasyonu Özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
