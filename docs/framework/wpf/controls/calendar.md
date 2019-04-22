---
title: Takvim
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: 9a64c6cd6fc1cc53383f2617f7a7a78959e87c4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124793"
---
# <a name="calendar"></a>Takvim
Bir takvim görsel bir takvim görünümünü kullanarak bir tarih seçmek üzere bir kullanıcı etkinleştirir.  
  
 A <xref:System.Windows.Controls.Calendar> denetimi kendi ya da açılan bir parçası olarak kullanılabilir bir <xref:System.Windows.Controls.DatePicker> denetimi. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DatePicker>.  
  
 Aşağıdaki iki resimde <xref:System.Windows.Controls.Calendar> seçimleri ve Kararma tarihleri biriyle ve görüntü olmadan denetler.  
  
 ![Takvim denetimlerinde](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Takvim denetimleri  
  
 Aşağıdaki tabloda, genellikle ilişkilendirilmiş olan görevler hakkında bilgi sağlar <xref:System.Windows.Controls.Calendar>.  
  
|Görev|Uygulama|  
|----------|--------------------|  
|Tarihleri belirtin, seçilemez.|Kullanım <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> özelliği.|  
|Sahip <xref:System.Windows.Controls.Calendar> görünen bir ay, tüm bir yıl veya on yıl.|Ayarlama <xref:System.Windows.Controls.Calendar.DisplayMode%2A> ay, yıl veya on özelliği.|  
|Kullanıcının bir tarih seçip olup, bir tarih aralığı veya birden çok aralık tarihleri belirtin.|Kullanım <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Tarih aralığını belirtin, <xref:System.Windows.Controls.Calendar> görüntüler.|Kullanım <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> ve <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> özellikleri.|  
|Geçerli tarihi vurgulanır olup olmadığını belirtin.|Kullanım <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> özelliği. Varsayılan olarak, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> olduğu `true`.|  
|Boyutunu değiştirme <xref:System.Windows.Controls.Calendar>.|Kullanım bir <xref:System.Windows.Controls.Viewbox> veya <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliğini bir <xref:System.Windows.Media.ScaleTransform>. Ayarlarsanız unutmayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini bir <xref:System.Windows.Controls.Calendar>, gerçek Takvim boyutunu değiştirmez.|  
  
 <xref:System.Windows.Controls.Calendar> Denetim, klavye veya fare kullanarak temel gezinme sağlar. Klavye ile gezinme aşağıdaki tabloda özetlenmiştir.  
  
|Tuş bileşimi|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Eylem|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|OKU|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> özelliği varsa <xref:System.Windows.Controls.Calendar.SelectionMode%2A> özelliği ayarlanmamış <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|OKU|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değişiklikleri <xref:System.Windows.Controls.Calendar.DisplayDate%2A> özelliği. Unutmayın <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|OKU|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Unutmayın <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|SHIFT + OK|<xref:System.Windows.Controls.CalendarMode.Month>|Varsa <xref:System.Windows.Controls.Calendar.SelectionMode%2A> ayarlı değil <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> veya <xref:System.Windows.Controls.CalendarSelectionMode.None>, seçili tarih aralığı genişletir.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın ilk gününe kadar günleri.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değişiklikleri <xref:System.Windows.Controls.Calendar.DisplayDate%2A> yılın ilk ay için. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|HOME|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> ilk on yıllık için. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın son günü.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değişiklikleri <xref:System.Windows.Controls.Calendar.DisplayDate%2A> yılın son ayını için. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> son on yılın için. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|CTRL + YUKARI OK|Tüm|Anahtarları sonraki daha büyük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Varsa <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Decade>, eylem yok.|  
|CTRL + AŞAĞI OK|Tüm|Anahtarları sonraki küçük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Varsa <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Month>, eylem yok.|  
|BOŞLUK veya ENTER|<xref:System.Windows.Controls.CalendarMode.Year> veya <xref:System.Windows.Controls.CalendarMode.Decade>|Anahtarları <xref:System.Windows.Controls.Calendar.DisplayMode%2A> için <xref:System.Windows.Controls.CalendarMode.Month> veya <xref:System.Windows.Controls.CalendarMode.Year> odaklanmış öğesi tarafından temsil edilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler](index.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
