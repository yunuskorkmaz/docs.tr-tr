---
title: Takvim Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: beba15f12b0ae2b819c641de9af8485767ad1a78
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373419"
---
# <a name="calendar-styles-and-templates"></a>Takvim Stilleri ve Şablonları
Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Calendar> denetimi. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için. Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Takvim bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Calendar> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Şu anda görüntülenen ayı veya yılı <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|İçeren paneli <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Takvim durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Calendar> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="calendaritem-parts"></a>CalendarItem bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarItem> denetimi.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Denetim kökü.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Takvim önceki sayfasına tıklatıldığında görüntülenen düğme.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Sonraki sayfaya takvimin tıklatıldığında görüntülenen düğme.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Ay modu, yıl modu ve on modu arasında geçişi sağlar düğmesi.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Ay modundayken içeriği barındırır.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Yıl veya on modunda olduğunda içeriği barındırır.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Kaplaması için devre dışı bırakılmış.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> , Görsel yapısını açıklar.|  
  
## <a name="calendaritem-states"></a>CalendarItem durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarItem> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal durumu|CommonStates|Varsayılan durumu.|  
|Devre dışı durumu|CommonStates|Takvim durumunu zaman <xref:System.Windows.UIElement.IsEnabled%2A> özelliği `false`.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton bölümleri  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Denetim herhangi bir adlandırılmış bölümü yok.  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarDayButton> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Devre dışı bırakıldı.|  
|Fareyi üzerine getirme|CommonStates|Fareyi üzerine getirildiği <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Basılan|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Basıldığında.|  
|Seçildi|SelectionStates|Düğmesi seçilir.|  
|Seçimi kaldırıldı|SelectionStates|Düğme seçili değil.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Bir düğme odak vardır.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Düğme odak yok.|  
|Odaklanmış|FocusStates|Bir düğme odak vardır.|  
|Plana odaklanmadan|FocusStates|Düğme odak yok.|  
|Etkin|ActiveStates|Düğme etkin değil.|  
|Etkin değil|ActiveStates|Düğme etkin değil.|  
|RegularDay|DayStates|Düğmeyi temsil etmez <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Bugün|DayStates|Düğme nesnesini temsil eden <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Düğmesini seçilebilir bir günü temsil eder.|  
|BlackoutDay|BlackoutDayStates|Düğmesi seçilemez bir günü temsil eder.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton bölümleri  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Denetim herhangi bir adlandırılmış bölümü yok.  
  
## <a name="calendarbutton-states"></a>CalendarButton durumları  
 Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarButton> denetimi.  
  
|VisualState adı|Visualstategroup'u adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Devre dışı bırakıldı.|  
|Fareyi üzerine getirme|CommonStates|Fareyi üzerine getirildiği <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Basılan|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Basıldığında.|  
|Seçildi|SelectionStates|Düğmesi seçilir.|  
|Seçimi kaldırıldı|SelectionStates|Düğme seçili değil.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Bir düğme odak vardır.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Düğme odak yok.|  
|Odaklanmış|FocusStates|Bir düğme odak vardır.|  
|Plana odaklanmadan|FocusStates|Düğme odak yok.|  
|Etkin|ActiveStates|Düğme etkin değil.|  
|Etkin değil|ActiveStates|Düğme etkin değil.|  
|Geçerli|ValidationStates|Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.|  
  
## <a name="calendar-controltemplate-example"></a>Takvim ControlTemplate Örneği  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Calendar> denetimi ve ilişkili tür.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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
