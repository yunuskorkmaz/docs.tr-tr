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
ms.openlocfilehash: 49d9ced42572ac06a4ff824ec41a59c14497d215
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460932"
---
# <a name="calendar-styles-and-templates"></a>Takvim Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.Calendar> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Takvim bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Calendar> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Tür|Açıklama|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|<xref:System.Windows.Controls.Calendar>Şu anda görüntülenen ay veya yıl.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Primitives.CalendarItem>içeren panel.|  
  
## <a name="calendar-states"></a>Takvim durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Calendar> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|----------------------|---------------------------|-----------------|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="calendaritem-parts"></a>CalendarItem bölümleri  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarItem> denetimi için adlandırılmış bölümler listelenmektedir.  
  
|Bölümüyle|Tür|Açıklama|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|Denetimin kökü.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Tıklandığında takvimin önceki sayfasını görüntüleyen düğme.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Tıklandığında takvimin sonraki sayfasını görüntüleyen düğme.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Ay modu, yıl modu ve on yıl modu arasında geçişe izin veren düğme.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Ay modundayken içeriği barındırır.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Yıl veya on yıl modunda içeriği barındırır.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Devre dışı durumu için yer paylaşımı.|  
|Daytitleşablonu|<xref:System.Windows.DataTemplate>|Görsel yapıyı tanımlayan <xref:System.Windows.DataTemplate>.|  
  
## <a name="calendaritem-states"></a>CalendarItem durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarItem> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Normal durum|Ortak durumlar|Varsayılan durum.|  
|Devre dışı durumu|Ortak durumlar|<xref:System.Windows.UIElement.IsEnabled%2A> özelliği `false`, takvimin durumu.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton bölümleri  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> denetiminde hiç adlandırılmış bölüm yok.  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarDayButton> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Olağan|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|<xref:System.Windows.Controls.Primitives.CalendarDayButton> devre dışı bırakıldı.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.Primitives.CalendarDayButton>yerleştirilir.|  
|Basılması|Ortak durumlar|<xref:System.Windows.Controls.Primitives.CalendarDayButton> basıldığında.|  
|Seçildiğinde|SelectionStates|Düğme seçilidir.|  
|Değilken|SelectionStates|Düğme seçili değil.|  
|Calendarbuttonodaklanmış|CalendarButtonFocusStates|Düğme odağa sahiptir.|  
|Calendarbuttonunodaklanmış|CalendarButtonFocusStates|Düğme odağa sahip değil.|  
|Diğinize|Odaklardaki durumlar|Düğme odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Düğme odağa sahip değil.|  
|Bkz|ActiveStates|Düğme etkin.|  
|Olmadan|ActiveStates|Düğme etkin değil.|  
|RegularDay|Gün cinsinden durumlar|Düğme <xref:System.DateTime.Today%2A?displayProperty=nameWithType>temsil etmez.|  
|Adresten|Gün cinsinden durumlar|Düğme <xref:System.DateTime.Today%2A?displayProperty=nameWithType>temsil eder.|  
|Normalgün|BlackoutDayStates|Düğme, seçilebilirler bir günü temsil eder.|  
|BlackoutDay|BlackoutDayStates|Düğme seçilebir günü temsil eder.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="calendarbutton-parts"></a>CalendarButton kısımları  
 <xref:System.Windows.Controls.Primitives.CalendarButton> denetiminde hiç adlandırılmış bölüm yok.  
  
## <a name="calendarbutton-states"></a>CalendarButton durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.CalendarButton> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Olağan|Ortak durumlar|Varsayılan durum.|  
|Devre dışı|Ortak durumlar|<xref:System.Windows.Controls.Primitives.CalendarButton> devre dışı bırakıldı.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi <xref:System.Windows.Controls.Primitives.CalendarButton>yerleştirilir.|  
|Basılması|Ortak durumlar|<xref:System.Windows.Controls.Primitives.CalendarButton> basıldığında.|  
|Seçildiğinde|SelectionStates|Düğme seçilidir.|  
|Değilken|SelectionStates|Düğme seçili değil.|  
|Calendarbuttonodaklanmış|CalendarButtonFocusStates|Düğme odağa sahiptir.|  
|Calendarbuttonunodaklanmış|CalendarButtonFocusStates|Düğme odağa sahip değil.|  
|Diğinize|Odaklardaki durumlar|Düğme odağa sahiptir.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Düğme odağa sahip değil.|  
|Bkz|ActiveStates|Düğme etkin.|  
|Olmadan|ActiveStates|Düğme etkin değil.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="calendar-controltemplate-example"></a>Takvim ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Calendar> denetimi ve ilişkili türler için <xref:System.Windows.Controls.ControlTemplate> nasıl tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
