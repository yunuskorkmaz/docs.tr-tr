---
title: MonthCalendar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734932"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi, kullanıcıların tarih bilgilerini görüntülemesi ve ayarlaması için sezgisel bir grafik arabirimi sunar. Denetimde bir takvim görüntülenir: seçilen tarih aralığı vurgulanmış şekilde, haftanın günleri altındaki sütunlarda düzenlenmiş, ayın numaralandırılmış günlerini içeren bir kılavuz. Ay başlığının her iki tarafındaki ok düğmelerine tıklayarak farklı bir ay seçebilirsiniz. Benzer <xref:System.Windows.Forms.DateTimePicker> denetiminden farklı olarak, bu denetimle birden fazla tarih seçebilirsiniz. <xref:System.Windows.Forms.DateTimePicker> denetimi hakkında daha fazla bilgi için bkz. [DateTimePicker denetimi](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>MonthCalendar denetimini yapılandırma  
 <xref:System.Windows.Forms.MonthCalendar> denetiminin görünümü yüksek oranda yapılandırılabilir. Varsayılan olarak, bugünün tarihi daire içinde görüntülenir ve kılavuzun alt kısmında de belirtilmiştir. <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> ve <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> özelliklerini `false`olarak ayarlayarak bu özelliği değiştirebilirsiniz. Ayrıca, <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`olarak ayarlayarak takvime hafta numaraları ekleyebilirsiniz. <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliğini ayarlayarak, yatay ve dikey olarak birden fazla ay görüntülenmiş olabilir. Varsayılan olarak, Pazar haftanın ilk günü olarak gösterilir, ancak <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> özelliği kullanılarak herhangi bir gün belirlenebilir.  
  
 Ayrıca, <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>ve <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> özelliklerine <xref:System.DateTime> nesneleri ekleyerek belirli tarihleri tek seferlik, yılda veya ayda kalın olarak görüntülenmek üzere ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms MonthCalendar denetimiyle belirli günleri kalın olarak görüntüleme](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 <xref:System.Windows.Forms.MonthCalendar> denetiminin anahtar özelliği <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, denetimde seçilen tarih aralığıdır. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> değeri, en fazla seçilecek gün sayısını aşamaz, <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> özelliğinde ayarlanır. Kullanıcının seçim yaptığı en erken ve en son tarihler <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> ve <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> özellikleri tarafından belirlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
