---
title: Takvim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 857f6b3be1467ec54fd27c76679279c0d0960690
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="calendar"></a>Takvim
Bir takvim visual Takvim görüntü kullanarak bir tarih seçmek bir kullanıcı sağlar.  
  
 A <xref:System.Windows.Controls.Calendar> denetimi kendi başına ya da aşağı açılan bir parçası olarak kullanılabilir bir <xref:System.Windows.Controls.DatePicker> denetim. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DatePicker>.  
  
 Aşağıdaki çizimde iki gösterir <xref:System.Windows.Controls.Calendar> denetimleri, biri seçimleri ve Kararma tarihleri diğeri olmadan.  
  
 ![Takvim denetimlerinde](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Takvim denetimleri  
  
 Aşağıdaki tabloda genellikle ilişkili olan görevler hakkında bilgi sağlayan <xref:System.Windows.Controls.Calendar>.  
  
|Görev|Uygulama|  
|----------|--------------------|  
|Tarihleri belirtin, seçilemez.|Kullanım <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> özelliği.|  
|Sahip <xref:System.Windows.Controls.Calendar> bir ay, bir yılın tamamı veya bir on görüntüleme.|Ayarlama <xref:System.Windows.Controls.Calendar.DisplayMode%2A> ay, yıl veya on özelliğine.|  
|Kullanıcı bir tarih olup seçebilir, bir tarih aralığı veya birden çok aralık tarihleri belirtin.|Kullanım <xref:System.Windows.Controls.Calendar.SelectionMode%2A>.|  
|Tarih aralığını belirtin, <xref:System.Windows.Controls.Calendar> görüntüler.|Kullanım <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> ve <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> özellikleri.|  
|Geçerli tarih vurgulanmış olup olmadığını belirtin.|Kullanım <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> özelliği. Varsayılan olarak, <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> olan `true`.|  
|Boyutu değiştirme <xref:System.Windows.Controls.Calendar>.|Kullanım bir <xref:System.Windows.Controls.Viewbox> veya <xref:System.Windows.FrameworkElement.LayoutTransform%2A> özelliğine bir <xref:System.Windows.Media.ScaleTransform>. Ayarlarsanız unutmayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini bir <xref:System.Windows.Controls.Calendar>, gerçek Takvim boyutunu değiştirmez.|  
  
 <xref:System.Windows.Controls.Calendar> Denetim klavye veya fare kullanarak temel gezinme sağlar. Aşağıdaki tabloda, klavye gezinti özetler.  
  
|Tuş bileşimini|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|Eylem|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|OK|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> özelliği, <xref:System.Windows.Controls.Calendar.SelectionMode%2A> özelliği ayarlı değil <xref:System.Windows.Controls.CalendarSelectionMode.None>.|  
|OK|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> özelliği. Unutmayın <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|OK|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A>. Unutmayın <xref:System.Windows.Controls.Calendar.SelectedDate%2A> değişmez.|  
|SHIFT + OK|<xref:System.Windows.Controls.CalendarMode.Month>|Varsa <xref:System.Windows.Controls.Calendar.SelectionMode%2A> ayarlanmazsa <xref:System.Windows.Controls.CalendarSelectionMode.SingleDate> veya <xref:System.Windows.Controls.CalendarSelectionMode.None>, seçili tarih aralığını genişletir.|  
|GİRİŞ|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın ilk günü için.|  
|GİRİŞ|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> yılın ilk ayı için. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|GİRİŞ|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> on ilk yılda. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|Değişiklikleri <xref:System.Windows.Controls.Calendar.SelectedDate%2A> geçerli ayın son günü.|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|Ayın değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> yılın son ayı. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|Yıl değerini değiştirir <xref:System.Windows.Controls.Calendar.DisplayDate%2A> on son yılda. <xref:System.Windows.Controls.Calendar.SelectedDate%2A> Değişmez.|  
|CTRL + YUKARI OK|tüm|Geçiş için sonraki büyük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Varsa <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Decade>, eylem yok.|  
|CTRL + AŞAĞI OK|tüm|Anahtarları sonraki küçük <xref:System.Windows.Controls.Calendar.DisplayMode%2A>. Varsa <xref:System.Windows.Controls.Calendar.DisplayMode%2A> zaten <xref:System.Windows.Controls.CalendarMode.Month>, eylem yok.|  
|Ara çubuğu veya ENTER|<xref:System.Windows.Controls.CalendarMode.Year>veya<xref:System.Windows.Controls.CalendarMode.Decade>|Anahtarlar <xref:System.Windows.Controls.Calendar.DisplayMode%2A> için <xref:System.Windows.Controls.CalendarMode.Month> veya <xref:System.Windows.Controls.CalendarMode.Year> odaklanmış öğesi tarafından temsil edilen.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimleri](../../../../docs/framework/wpf/controls/index.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
