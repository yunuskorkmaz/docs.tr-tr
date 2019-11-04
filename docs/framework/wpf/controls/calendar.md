---
title: Takvim
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460813"
---
# <a name="calendar"></a>Takvim
Takvim, bir kullanıcının görsel takvim görüntüsü kullanarak bir tarih seçmesini sağlar.  
  
 Bir <xref:System.Windows.Controls.Calendar> denetimi kendi kendine veya bir <xref:System.Windows.Controls.DatePicker> denetiminin açılan bir parçası olarak kullanılabilir. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DatePicker>.  
  
 Aşağıdaki çizimde, biri seçim ve Kararma tarihleri ve bir olmadan olmak üzere iki <xref:System.Windows.Controls.Calendar> denetimi gösterilmektedir.  
  
 ![Takvim denetimleri](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Takvim denetimleri  
  
 Aşağıdaki tabloda, genellikle <xref:System.Windows.Controls.Calendar>ilişkili görevler hakkında bilgi verilmektedir.  
  
|Görev|Uygulama|  
|----------|--------------------|  
|Seçileme tarihleri belirtin.|<xref:System.Windows.Controls.Calendar.BlackoutDates%2A> özelliğini kullanın.|  
|<xref:System.Windows.Controls.Calendar> bir ay, bir yıl boyunca veya yılda bir yıl görüntülenmesini sağlayabilirsiniz.|<xref:System.Windows.Controls.Calendar.DisplayMode%2A> özelliğini ay, yıl veya on yıl olarak ayarlayın.|  
|Kullanıcının bir tarih, bir tarih aralığı veya birden çok tarih aralığı seçip seçmeyeceğini belirtin.|<xref:System.Windows.Controls.Calendar.SelectionMode%2A>kullanın.|  
|<xref:System.Windows.Controls.Calendar> görüntülediği tarih aralığını belirtin.|<xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> ve <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> özelliklerini kullanın.|  
|Geçerli tarihin vurgulanıp vurgulanmadığını belirtin.|<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> özelliğini kullanın. Varsayılan olarak, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> `true`.|  
|<xref:System.Windows.Controls.Calendar>boyutunu değiştirin.|<xref:System.Windows.Controls.Viewbox> kullanın veya <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliğini <xref:System.Windows.Media.ScaleTransform>olarak ayarlayın. Bir <xref:System.Windows.Controls.Calendar><xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini ayarlarsanız, gerçek takvimin boyutunu değiştirmediğini unutmayın.|  
  
 <xref:System.Windows.Controls.Calendar> denetimi, fare veya klavyeyi kullanarak temel gezinme sağlar. Aşağıdaki tabloda klavye gezintisi özetlenmektedir.  
  
|Anahtar birleşimi|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Eylem|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|OKUN|<xref:System.Windows.Controls.CalendarMode.Month>|<xref:System.Windows.Controls.Calendar.SelectionMode%2A> özelliği <xref:System.Windows.Controls.CalendarSelectionMode.None>olarak ayarlanmamışsa <xref:System.Windows.Controls.Calendar.SelectedDate%2A> özelliğini değiştirir.|  
|OKUN|<xref:System.Windows.Controls.CalendarMode.Year>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> özelliğinin ayını değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmediğini unutmayın.|  
|OKUN|<xref:System.Windows.Controls.CalendarMode.Decade>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A>yılını değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmediğini unutmayın.|  
|SHIFT + ok|<xref:System.Windows.Controls.CalendarMode.Month>|<xref:System.Windows.Controls.Calendar.SelectionMode%2A> <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> veya <xref:System.Windows.Controls.CalendarSelectionMode.None>olarak ayarlanmamışsa, seçili tarih aralığını genişletir.|  
|SAYFA|<xref:System.Windows.Controls.CalendarMode.Month>|<xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın ilk gününe değiştirir.|  
|SAYFA|<xref:System.Windows.Controls.CalendarMode.Year>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> ayını yılın ilk ayında değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|SAYFA|<xref:System.Windows.Controls.CalendarMode.Decade>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> yılını yılın ilk yılına değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|<xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın son gününe değiştirir.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> ayını yılın son ayına değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> yıl yılını en son yılda bulunan yıl olarak değiştirir. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|CTRL + YUKARı OK|Kaydedilmemiş|Sonraki büyük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>geçer. <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Decade>, hiçbir eylem yoktur.|  
|CTRL + AŞAĞı OK|Kaydedilmemiş|Sonraki küçük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>geçer. <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Month>, hiçbir eylem yoktur.|  
|ARA çubuğu veya ENTER|<xref:System.Windows.Controls.CalendarMode.Year> veya <xref:System.Windows.Controls.CalendarMode.Decade>|<xref:System.Windows.Controls.Calendar.DisplayMode%2A> odaklanmış öğe tarafından temsil edilen <xref:System.Windows.Controls.CalendarMode.Month> veya <xref:System.Windows.Controls.CalendarMode.Year> geçirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler](index.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
