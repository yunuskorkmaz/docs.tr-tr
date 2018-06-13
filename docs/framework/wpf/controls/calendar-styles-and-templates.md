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
ms.openlocfilehash: 5398828d1526436ab5abbbd2e87515018b0cd8bf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457530"
---
# <a name="calendar-styles-and-templates"></a>Takvim Stilleri ve Şablonları
Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Calendar> denetim. Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için. Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Takvim bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Calendar> denetim.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Şu anda görüntülenen ay veya yıl <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|İçeren paneli <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Takvim durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Calendar> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="calendaritem-parts"></a>CalendarItem bölümleri  
 Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.CalendarItem> denetim.  
  
|Bölümü|Tür|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Denetim kökü.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Önceki sayfaya takvimin tıklandığında görüntüleyen düğmesi.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Sonraki sayfaya takvimin tıklandığında görüntüleyen düğmesi.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Ay modu, yıl modu ve on modu arasında geçiş yapma sağlayan düğmeyi.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Ay modunda içerik barındırır.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|İçerik yıl veya on modundayken barındırır.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Devre dışı durumunu katmana.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> Görsel yapısını açıklar.|  
  
## <a name="calendaritem-states"></a>CalendarItem durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.CalendarItem> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal durumu|CommonStates|Varsayılan durumu.|  
|Devre dışı durum|CommonStates|Takvim durumunu zaman <xref:System.Windows.UIElement.IsEnabled%2A> özelliği `false`.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton bölümleri  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> Denetim adlandırılmış tüm bölümler sahip değil.  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.CalendarDayButton> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Devre dışı bırakılır.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerine getirildiği <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Basılı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> Basıldığında.|  
|Seçili|SelectionStates|Düğmesi seçilir.|  
|Seçilmemiş|SelectionStates|Düğme seçili değil.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Düğme odağa sahip.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Düğme odağa sahip değil.|  
|Odaklanmış|FocusStates|Düğme odağa sahip.|  
|Odaksız|FocusStates|Düğme odağa sahip değil.|  
|Etkin|ActiveStates|Düğme etkindir.|  
|Etkin olmayan|ActiveStates|Düğmesi etkin değildir.|  
|RegularDay|DayStates|Düğmeyi temsil etmiyor <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Bugün|DayStates|Düğmeyi temsil <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Düğmesini seçilebilir bir günü temsil eder.|  
|BlackoutDay|BlackoutDayStates|Düğme seçilemez bir günü temsil eder.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton bölümleri  
 <xref:System.Windows.Controls.Primitives.CalendarButton> Denetim adlandırılmış tüm bölümler sahip değil.  
  
## <a name="calendarbutton-states"></a>CalendarButton durumları  
 Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.CalendarButton> denetim.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal|CommonStates|Varsayılan durumu.|  
|Devre dışı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Devre dışı bırakılır.|  
|Fare üzerinde|CommonStates|Fare işaretçisini üzerine getirildiği <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Basılı|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> Basıldığında.|  
|Seçili|SelectionStates|Düğmesi seçilir.|  
|Seçilmemiş|SelectionStates|Düğme seçili değil.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Düğme odağa sahip.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Düğme odağa sahip değil.|  
|Odaklanmış|FocusStates|Düğme odağa sahip.|  
|Odaksız|FocusStates|Düğme odağa sahip değil.|  
|Etkin|ActiveStates|Düğme etkindir.|  
|Etkin olmayan|ActiveStates|Düğmesi etkin değildir.|  
|Geçerli|ValidationStates|Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.|  
  
## <a name="calendar-controltemplate-example"></a>Takvim ControlTemplate Örneği  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Calendar> denetimi ve ilişkili türler.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim Stilleri ve Şablonları](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
