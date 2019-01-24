---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 34df32ceecf66061b74834dcecdef8a080b7af34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565611"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Denetime izin verir ya da metin alanına yazarak veya açılan listesi kullanarak bir tarih seçmek üzere kullanıcı <xref:System.Windows.Controls.Calendar> denetimi.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.DatePicker>.  
  
 ![DatePicker denetimi](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker denetimi  
  
 Çoğu bir <xref:System.Windows.Controls.DatePicker> denetimin özelliklerini olan yerleşik yönetmek için <xref:System.Windows.Controls.Calendar>ve eşdeğer özelliği için aynı şekilde işlev <xref:System.Windows.Controls.Calendar>. Özellikle, <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> özellikleri öğesine aynı şekilde işlev kendi <xref:System.Windows.Controls.Calendar> ortaklarınıza. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.Calendar>.  
  
 Kullanıcılar, ayarlar doğrudan bir metin alanı, bir tarih yazabilirsiniz <xref:System.Windows.Controls.DatePicker.Text%2A> özelliği. Varsa <xref:System.Windows.Controls.DatePicker> girilen dize geçerli bir tarih dönüştürülemiyor <xref:System.Windows.Controls.DatePicker.DateValidationError> olayı yükseltilir. Varsayılan olarak, bu ancak bir olay işleyicisi için bir özel duruma neden <xref:System.Windows.Controls.DatePicker.DateValidationError> ayarlayabilirsiniz <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> özelliğini `false` ve bir özel durum harekete öğesinden engelleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Denetimler](../../../../docs/framework/wpf/controls/index.md)
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
