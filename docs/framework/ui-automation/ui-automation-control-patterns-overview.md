---
title: UI Otomasyon Denetim Düzenlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: 12bfe994e02e1a330cc543ca1afd21ddf32dac66
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673684"
---
# <a name="ui-automation-control-patterns-overview"></a>UI Otomasyon Denetim Düzenlerine Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış sunar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim desenleri. Denetim desenlerini kategorilere ayırmak ve denetim türünü veya denetimin görünümünü bağımsız bir denetimin işlevselliği göstermek için bir yol sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ortak denetim davranışlarını temsil etmek için modelleri kullanır denetler. Örneğin, (düğme gibi) çağrılabilir denetimleri ve kaydırma çubukları (örneğin, liste kutuları, liste görünümleri veya birleşik giriş kutuları gibi) sahip denetimler için kaydırma denetim düzeni için Invoke denetim desenini kullanın. Her denetim düzeni ayrı bir işlevi temsil ettiğinden belirli bir denetim tarafından desteklenen işlevlerin tam kümesini tanımlamak için birleştirilebilir.  
  
> [!NOTE]
>  Denetimleri bir araya — sağlayan alt denetimler ile oluşturulan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] için üst öğe tarafından kullanıma sunulan işlevsellikten — normalde her alt denetimle ilişkili tüm denetim düzenleri uygulamalıdır. Sırayla bu aynı denetim düzenleri alt denetimlerin uygulanması gerekli değildir.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>UI Otomasyon denetim düzeni bileşenleri  
 Yöntemleri, özellikleri, olayları ve ayrı bir denetimde kullanılabilen işlevler tanımlamak için gerekli ilişkileri denetim düzenleri desteği.  
  
-   Öğenin yapısı içinde bir UI Otomasyonu öğesi ve kendi üst, alt ve eşdüzey arasındaki ilişkiyi açıklar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.  
  
-   Yöntemler, denetimi işlemek UI Otomasyon istemcileri sağlar.  
  
-   Özellikler ve olaylar denetim deseninin işlevleri hakkında bilgi yanı sıra denetim durumu hakkında bilgi sağlar.  
  
 Denetim desenlerini ilişkili [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] arabirimleri ile ilgili olarak [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] nesneleri. İçinde [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], hangi arabirimlerin isteyin ve ardından o arabirimlerin erişim işlevine bir nesne sorgulayabilirsiniz. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], UI Otomasyon istemcileri, isteğe bağlı olarak hangi denetimin destekler desenler bir denetim isteyin ve denetim özellikleri, yöntemleri, olay ve yapıları tarafından desteklenen denetim düzenleri ortaya aracılığıyla etkileşim. Örneğin, bir çok satırlı düzenleme kutusu için UI Otomasyon sağlayıcıları uygulamak <xref:System.Windows.Automation.Provider.IScrollProvider>. Ne zaman bir istemci bilir, bir <xref:System.Windows.Automation.AutomationElement> destekler <xref:System.Windows.Automation.ScrollPattern> denetim düzeni, özellikleri, yöntemleri ve olayları bu denetim düzeni tarafından kullanıma sunulan denetimi işlemek veya denetimi ile ilgili bilgilere erişmek için kullanabilirsiniz.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>UI Otomasyonu sağlayıcıları ve istemciler  
 UI Otomasyonu sağlayıcıları, belirli bir denetim tarafından desteklenen işlevlerin uygun davranışını ortaya çıkarmak için Denetim desenleri uygulayın.  
  
 UI Otomasyon istemcileri erişim yöntemleri ve özellikleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzeni sınıfları ve hakkında bilgi almak için bunları kullanmayı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], veya işlemek için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Bu denetim düzeni sınıfları bulunan <xref:System.Windows.Automation> ad alanı (örneğin, <xref:System.Windows.Automation.InvokePattern> ve <xref:System.Windows.Automation.SelectionPattern>).  
  
 İstemcilerin kullandığı <xref:System.Windows.Automation.AutomationElement> yöntemleri (gibi <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) veya [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] erişmek için erişimciler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desen özellikleri. Her denetim düzeni sınıfı alan bir üyenin (örneğin, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> veya <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>), bu denetim desenini tanımlar ve bir parametre olarak geçirilen <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bu deseni için alınacak bir <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Dinamik Denetim desenleri  
 Bazı denetimler, her zaman aynı denetim düzenleri kümesini desteklemez. Denetim desenleri için UI Otomasyonu istemci kullanılabilir olduklarında desteklenen olarak kabul edilir. Örneğin, çok satırlı dikey yalnızca kendi görüntülenebilir alanında görüntülenebilenden metin daha fazla satır içerdiğinde Kaydırma kutusu etkinleştirir düzenleyin. Kaydırma artık gerekli olacak şekilde yeterli metin kaldırıldığında kaydırmayı devre dışı bırakıldı. Bu örnekte, ScrollPattern'ı denetim desenini (ne kadar metin düzenleme kutusu içinde) denetimin geçerli durumuna bağlı olarak dinamik olarak desteklenir.  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Denetim düzeni sınıfları ve arabirimleri  
 Aşağıdaki tabloda açıklanmıştır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri. Tablo, ayrıca bunları uygulama UI Otomasyon sağlayıcıları tarafından kullanılan arabirimlere yanı sıra denetim düzenleri erişmek için UI Otomasyon istemcileri tarafından kullanılan sınıflar listelenir.  
  
|Denetim düzeni sınıfı|Sağlayıcı arabirimi|Açıklama|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Yerleştirme bir kapsayıcıda yerleşik denetimler için kullanılır. Örneğin, araç çubukları veya aracı paletleri.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Genişletilmiş veya daraltılmış denetimleri için kullanılır. Örneğin, menü uygulamada gibi öğeleri **dosya** menüsü.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Kılavuz işleve boyutlandırma ve taşıma için belirtilen bir hücre gibi denetimler için kullanılır. Örneğin, büyük simge görünümünde Windows Gezgini veya üst bilgilerinde olmadan basit tablolar [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Kılavuzlar hücrelerde denetimleri için kullanılır. Tek tek hücrelere GridItem düzeni desteklemelidir. Örneğin, her hücreye [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] ayrıntı görüntüle.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Bir düğme gibi çağrılabilir denetimleri için kullanılır.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Birden fazla aynı bilgileri, veri veya alt kümesini temsilleri arasında geçiş yapabilirsiniz denetimleri için kullanılır. Örneğin, bir liste görünümü denetimi veri küçük resim, kutucuk, simge, liste veya Ayrıntılı Görünüm kullanılabilir olduğu.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bir denetime uygulanabilen değerleri aralığına sahip denetimler için kullanılır. Örneğin, aralığı 1-12 ay sunan başka bir değer değiştirici denetim sahip olurken yıl içeren bir değer değiştirici denetim 1900 2010 için bir dizi olabilir.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Kaydırabileceği denetimleri için kullanılır. Örneğin, bir denetimi, denetimin görüntülenebilir bölümünde görüntülenebilecek olandan daha fazla bilgi olduğunda, etkin olan kaydırma çubukları vardır.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Bireysel öğeleri kayan bir listede olan denetimler için kullanılır. Örneğin, kaydırma listesinde, bir birleşik giriş kutusu denetimi gibi öğeler içeren bir liste denetim.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Seçim kapsayıcı denetimleri için kullanılır. Örneğin, liste kutuları ve birleşik giriş kutuları.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Seçim kapsayıcı denetimleri, liste kutuları ve birleşik giriş kutuları gibi tek tek öğeleri için kullanılır.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Bir kılavuz olan denetimler için kullanılan üstbilgi bilgilerinin yanı sıra. Örneğin, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] çalışma.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Bir tablodaki öğeleri için kullanılır.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Düzenleme denetimleri ve metinsel bilgi sunan belgeler için kullanılır.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Denetimler için durumu burada açılıp kapatılabilir kullanılır. Örneğin, onay kutularını ve checkable menü öğeleri.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Yeniden boyutlandırılmış, taşınabilir, döndürülen ve denetimler için kullanılır. Dönüşüm denetim düzeni için genel kullanımlar, tasarımcılar, form, grafik düzenleyicilerden ve çizim uygulamaları ' dir.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Değerini alma veya bir değer aralığını desteklemeyen denetimleri ayarlama etmesine olanak tanır. Örneğin, bir tarih saat Seçici.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Windows, bir temel kavram için özel bilgiler sunan [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] işletim sistemi. Windows denetimleri örnekler en üst düzey uygulama windows ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], vb.), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt pencereler ve iletişim kutuları.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
