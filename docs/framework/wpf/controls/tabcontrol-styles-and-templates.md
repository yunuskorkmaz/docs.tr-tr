---
title: TabControl Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
ms.openlocfilehash: e38756c5f266abc16b99f2359f8a87460d5d9450
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155382"
---
# <a name="tabcontrol-styles-and-templates"></a>TabControl Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.TabControl> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="tabcontrol-parts"></a>TabControl bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.TabControl> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_SelectedContentHost|<xref:System.Windows.Controls.ContentPresenter>|Şu anda seçili içeriğini gösteren nesne <xref:System.Windows.Controls.TabItem>.|  
  
 Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.TabControl>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.TabControl>; <xref:System.Windows.Controls.ScrollViewer> denetimi içinde kaydırma sağlar).  Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, size gereken <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.  
  
## <a name="tabcontrol-states"></a>TabControl durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TabControl> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="tabitem-parts"></a>TabItem bölümleri  
 <xref:System.Windows.Controls.TabItem> Denetim herhangi bir adlandırılmış bölümü yok.  
  
## <a name="tabitem-states"></a>TabItem durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TabItem> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|Varsayılan durumu.|  
|Fareyi üzerine getirme|CommonStates|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Devre dışı|CommonStates|Denetim devre dışıdır.|  
|Odaklanmış|FocusStates|Denetim odağa sahip.|  
|Plana odaklanmadan|FocusStates|Denetim odağa sahip değil.|  
|Seçildi|SelectionStates|Denetimin seçili olduğunu.|  
|Seçimi kaldırıldı|SelectionStates|Denetimin seçili değil.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="tabcontrol-controltemplate-example"></a>TabControl ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TabControl> ve <xref:System.Windows.Controls.TabItem> kontrol eder.  
  
 [!code-xaml[ControlTemplateExamples#TabControl](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
 Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
