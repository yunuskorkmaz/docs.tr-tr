---
title: "MonthCalendar Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a22667e4227067dfbf0baaad1838ab520e0ac7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi görüntülemek ve tarih bilgisini ayarlamak kullanıcılar için sezgisel bir grafik arabirim sağlar. Bir Takvim denetimi görüntüler: Seçili tarih aralığına göre vurgulanmış haftanın günleri altında sütunlardaki düzenlenmiş ayın numaralı gün içeren bir kılavuz. Her iki tarafında yer ay resim yazısı ok düğmelerini tıklayarak farklı bir ay seçebilirsiniz. Benzer aksine <xref:System.Windows.Forms.DateTimePicker> denetim, bu denetimi ile birden fazla tarih seçebilirsiniz. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DateTimePicker> denetlemek için bkz: [DateTimePicker denetimi](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## <a name="configuring-the-monthcalendar-control"></a>MonthCalendar denetimi yapılandırma  
 <xref:System.Windows.Forms.MonthCalendar> Denetiminin görünüşünü yüksek oranda yapılandırılabilir. Varsayılan olarak, bugünün tarihini yuvarlak içine alınmıştır olarak gösterilir ve kılavuz alt kısmında da Not edilir. Bu özellik ayarlayarak değiştirebileceğiniz <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> ve <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> özelliklerine `false`. Ayarlayarak takvime hafta numaralarını ekleyebilirsiniz <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğine `true`. Ayarlayarak <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliği, birden çok ay yatay ve dikey olarak görüntülenen sahip olabilir. Varsayılan olarak, Pazar haftanın ilk günü gösterilir, ancak herhangi bir gün kullanarak belirlenebilir <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> özelliği.  
  
 Ayrıca belirli tarihleri görüntülenmesini ekleyerek bir seferliğine, yıllık veya aylık olarak kalın ayarlayabilirsiniz <xref:System.DateTime> nesneleri <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, ve <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> özellikleri. Daha fazla bilgi için bkz: [nasıl yapılır: görüntü belirli günleri kalın Windows Forms MonthCalendar denetimi ile](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 Anahtar özelliği <xref:System.Windows.Forms.MonthCalendar> denetimi <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, denetim içinde seçilen tarih aralığı. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> Değeri, maksimum kümesinde seçilebilir gün sayısını aşamaz <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> özelliği. Kullanıcı seçebilir erken ve en son tarihleri tarafından belirlenen <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> ve <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> özellikleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MonthCalendar>  
 [MonthCalendar Denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
