---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> Denetimi sağlar kullanıcıya bir metin alanı içine ya da yazarak veya bir açılan kullanarak bir tarih seçin <xref:System.Windows.Controls.Calendar> denetim.  
  
 Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.DatePicker>.  
  
 ![DatePicker denetim](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker denetimi  
  
 Çoğu bir <xref:System.Windows.Controls.DatePicker> denetimin özelliklerdir yerleşik yönetmek için <xref:System.Windows.Controls.Calendar>ve eşdeğer özelliğinde aynı işleve <xref:System.Windows.Controls.Calendar>. Özellikle, <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> özellikleri işlev aynı için kendi <xref:System.Windows.Controls.Calendar> ortaklarınıza. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.Calendar>.  
  
 Kullanıcılar, ayarlar doğrudan bir metin alanı, bir tarih yazabilirsiniz <xref:System.Windows.Controls.DatePicker.Text%2A> özelliği. Varsa <xref:System.Windows.Controls.DatePicker> girilen dizesi geçerli bir tarih dönüştürülemiyor <xref:System.Windows.Controls.DatePicker.DateValidationError> olay harekete geçirilen. Varsayılan olarak, bu ancak bir olay işleyicisi için bir özel durum oluşur <xref:System.Windows.Controls.DatePicker.DateValidationError> ayarlayabilirsiniz <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> özelliğine `false` ve ortaya çıkan gelen bir özel durum engeller.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimleri](../../../../docs/framework/wpf/controls/index.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
