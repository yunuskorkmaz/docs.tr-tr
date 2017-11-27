---
title: "DateTimePicker Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a97eecc43614c84867e9dbdd527dbebd7dfd426e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> kullanıcının tarihleri veya saatleri listesinden tek bir öğe seçmesine izin verir. Bir tarihi temsil etmek için kullanıldığında, iki parça halinde görüntülenir: metin ve listenin yanındaki aşağı oka tıkladığınızda görüntülenen bir kılavuz temsil edilen bir tarihle aşağı açılan liste. Kılavuz benzer <xref:System.Windows.Forms.MonthCalendar> birden çok tarihi seçmek için kullanılan denetim. Daha fazla bilgi için <xref:System.Windows.Forms.MonthCalendar> denetlemek için bkz: [MonthCalendar denetimine genel bakış](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 İsterseniz <xref:System.Windows.Forms.DateTimePicker> çekme veya tarihleri yerine zamanlarını düzenleme için bir denetim olarak görünecek şekilde ayarlanması <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliğine `true` ve <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğine <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Daha fazla bilgi için bkz: [nasıl yapılır: DateTimePicker denetimiyle görüntü süresi](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Zaman <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> özelliği ayarlanmış `true`, seçilen tarihten denetiminde yanındaki onay kutusu görüntülenir. Onay kutusu işaretlendiğinde, seçilen tarih-saat değeri güncelleştirilebilir. Onay kutusu boş olduğunda, değerin kullanılamaz görüntülenir.  
  
 Denetimin <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> ve <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> özellikleri tarihler ve saatler aralığını belirler. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Özelliği, geçerli tarih ve saat Denetimi ayarlanmış içerir. Ayrıntılar için bkz [nasıl yapılır: ayarlama ve Windows Forms DateTimePicker denetimi ile tarihleri dönmek](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Tarafından belirlenen dört biçimlerde değerleri görüntülenen <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, veya <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Özel bir biçim seçtiyseniz ayarlamalısınız <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> uygun bir dize özelliği. Ayrıntılar için bkz [nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [Nasıl yapılır: tarihleri Windows Forms DateTimePicker denetimi ayarlama ve döndürme](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
