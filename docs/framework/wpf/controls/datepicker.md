---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460360"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> denetimi, kullanıcının bir metin alanına yazarak veya açılan <xref:System.Windows.Controls.Calendar> denetimini kullanarak bir tarih seçmesini sağlar.  
  
 Aşağıdaki çizimde bir <xref:System.Windows.Controls.DatePicker>gösterilmektedir.  
  
 ![DatePicker denetimi](./media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker denetimi  
  
 <xref:System.Windows.Controls.DatePicker> denetiminin özelliklerinin birçoğu yerleşik <xref:System.Windows.Controls.Calendar>yönetmeye yöneliktir ve <xref:System.Windows.Controls.Calendar>eşdeğer özelliği ile aynı şekilde çalışır. Özellikle, <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>ve <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> özellikleri <xref:System.Windows.Controls.Calendar> karşılıklarıyla aynı şekilde çalışır. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.Calendar>.  
  
 Kullanıcılar, <xref:System.Windows.Controls.DatePicker.Text%2A> özelliğini ayarlayan metin alanına doğrudan bir tarih yazabilir. <xref:System.Windows.Controls.DatePicker> girilen dizeyi geçerli bir tarihe dönüştüremediğinden, <xref:System.Windows.Controls.DatePicker.DateValidationError> olayı tetiklenir. Bu, varsayılan olarak bir özel duruma neden olur, ancak <xref:System.Windows.Controls.DatePicker.DateValidationError> için bir olay işleyicisi <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> özelliğini `false` olarak ayarlayabilir ve bir özel durumun oluşmasını engelleyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler](index.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
