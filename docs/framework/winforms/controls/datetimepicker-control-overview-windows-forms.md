---
title: DateTimePicker Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 1d2e286e3ce91c722be24f059a874b9db5f2ba82
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703187"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimi kullanıcının tarihleri veya saatleri listesinden tek bir öğe seçmesine olanak sağlar. Bir tarihi temsil etmek için kullanılan iki parça halinde görünür: metin ve listenin yanındaki aşağı oka tıkladığınızda görüntülenen bir kılavuz temsil tarihi olan bir açılan liste. Kılavuz benzer <xref:System.Windows.Forms.MonthCalendar> birden çok tarihlerini seçmek için kullanılabilecek bir denetim. Daha fazla bilgi için <xref:System.Windows.Forms.MonthCalendar> denetlemek için bkz: [MonthCalendar denetimine genel bakış](monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 İsterseniz <xref:System.Windows.Forms.DateTimePicker> çekme veya tarihleri yerine zamanlarını düzenleme için bir denetim olarak görüntülenecek şekilde ayarlayabileceğiniz <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> özelliğini `true` ve <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğini <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Daha fazla bilgi için [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](how-to-display-time-with-the-datetimepicker-control.md).  
  
 Zaman <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> özelliği `true`, seçilen tarihten denetiminde yanında bir onay kutusu görüntülenir. Seçilen tarih-saat değeri, onay kutusu işaretli olduğunda güncelleştirilebilir. Onay kutusu boş olduğunda, değer kullanılamaz olarak görünür.  
  
 Denetimin <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> ve <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> özellikleri tarih ve saat aralığını belirler. <xref:System.Windows.Forms.DateTimePicker.Value%2A> Özelliğini içeren geçerli tarih ve saat denetimini ayarlayın. Ayrıntılar için bkz [nasıl yapılır: Tarih ile Windows Forms DateTimePicker denetimi ayarlama ve döndürme](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Değerler tarafından ayarlanan dört biçimleri görüntülenebilir <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği: <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, veya <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Özel bir biçim seçtiyseniz ayarlamalısınız <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğini uygun bir dize. Ayrıntılar için bkz [nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [Nasıl yapılır: Windows Forms DateTimePicker denetimi ile ayarlanmış ve dönüş tarihleri](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
