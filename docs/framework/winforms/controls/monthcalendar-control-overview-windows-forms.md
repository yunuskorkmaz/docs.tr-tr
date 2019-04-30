---
title: MonthCalendar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 8928a78735392920d893661c70554bd35eba2886
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768491"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi görüntülemek ve tarih bilgisini ayarlamak kullanıcılar için sezgisel bir grafik arabirim sağlar. Bir Takvim denetimi görüntüler: ayın sütunlarındaki haftanın günlerini seçili vurgulanmış tarih aralığı ile altında düzenlenmiş numaralı gün içeren bir kılavuz. Farklı bir ay, aylık resim yazısı her iki tarafındaki oka düğmelere tıklayarak seçebilirsiniz. Benzer aksine <xref:System.Windows.Forms.DateTimePicker> denetimi, bu denetimi ile birden fazla tarih seçebilirsiniz. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DateTimePicker> denetlemek için bkz: [DateTimePicker denetimi](datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>MonthCalendar denetimi yapılandırma  
 <xref:System.Windows.Forms.MonthCalendar> Denetimin görünümü, yüksek oranda yapılandırılabilir. Varsayılan olarak, bugünün tarihini daire içinde olarak görüntülenir ve kılavuz alt kısmında da belirtilir. Bu özellik ayarlayarak değiştirebilirsiniz <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> ve <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> özelliklerine `false`. Ayarlayarak takvime hafta sayıları ekleyebilirsiniz <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`. Ayarlayarak <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliği, birden çok ay yatay ve dikey olarak görüntülenen sahip olabilir. Varsayılan olarak, Pazar haftanın ilk günü gösterilir, ancak herhangi bir gün kullanarak belirlenebilir <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> özelliği.  
  
 Ayrıca belirli tarihleri görüntülenecek ekleyerek bir seferliğine yıllık veya aylık olarak kalın ayarlayabilirsiniz <xref:System.DateTime> nesneleri için <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, ve <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> özellikleri. Daha fazla bilgi için [nasıl yapılır: Windows ile belirli günleri kalın olarak görüntüleme Forms MonthCalendar denetiminde](display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Anahtar özelliği <xref:System.Windows.Forms.MonthCalendar> denetimi <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, denetim içinde seçilen tarih aralığı. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Kümesinde seçilebilir gün sayısı değeri aşamaz <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> özelliği. Kullanıcı seçebilir erken ve en son tarihlerini tarafından belirlenen <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> ve <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> özellikleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
