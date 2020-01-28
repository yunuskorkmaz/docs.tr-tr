---
title: DateTimePicker Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746932"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimi, kullanıcının tarih veya saat listesinden tek bir öğe seçmesine izin verir. Bir tarihi temsil etmek için kullanıldığında, iki bölümden oluşur: metinde temsil edilen bir tarih ve listenin yanındaki aşağı oka tıkladığınızda görüntülenen bir kılavuz. Kılavuz, birden çok tarih seçmek için kullanılabilecek <xref:System.Windows.Forms.MonthCalendar> denetimi gibi görünür. <xref:System.Windows.Forms.MonthCalendar> denetimi hakkında daha fazla bilgi için bkz. [MonthCalendar denetimine genel bakış](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 <xref:System.Windows.Forms.DateTimePicker> tarihler yerine çekme veya düzenlemeyle ilgili bir denetim olarak görünmesini istiyorsanız, <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliğini `true` ve <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği <xref:System.Windows.Forms.DateTimePickerFormat.Time>olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](how-to-display-time-with-the-datetimepicker-control.md).  
  
 <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> özelliği `true`olarak ayarlandığında, denetimde seçili tarihin yanında bir onay kutusu görüntülenir. Onay kutusu işaretlendiğinde, seçilen tarih-saat değeri güncellenebilir. Onay kutusu boş olduğunda, değer kullanılamaz görüntülenir.  
  
 Denetimin <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> ve <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> özellikleri tarih ve saat aralığını belirlemede. <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği, denetimin ayarlandığı geçerli tarih ve saati içerir. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms DateTimePicker denetimi Ile tarihleri ayarlama ve döndürme](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Değerler, <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği tarafından ayarlanan dört biçimde görüntülenebilir: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>veya <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Özel bir biçim seçilirse, <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğini uygun bir dize olarak ayarlamanız gerekir. Ayrıntılar için bkz. [nasıl yapılır: Windows Forms DateTimePicker denetimi Ile özel biçimde tarih görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
