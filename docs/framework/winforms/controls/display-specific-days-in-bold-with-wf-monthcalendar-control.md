---
title: MonthCalendar denetimiyle belirli günleri kalın olarak görüntüle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: 377eb76f562fff20aae2136ddb7130516d2d76f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745888"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi günleri, tek tarihler veya tekrarlayan bir şekilde kalın türde gösterebilir. Bu işlem, tatiller ve hafta sonları gibi özel tarihlere dikkat çekmek için yapabilirsiniz.  
  
 Üç özellik bu özelliği denetler. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> özelliği tek tarihleri içerir. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> özelliği, her yıl kalın olarak görünen tarihleri içerir. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> özelliği, her ay kalın olarak görünen tarihleri içerir. Bu özelliklerin her biri, <xref:System.DateTime> nesnelerden oluşan bir dizi içerir. Bu listelerden birini bir tarih eklemek veya kaldırmak için <xref:System.DateTime> nesnesi eklemeniz veya kaldırmanız gerekir.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Bir tarihin kalın türde görünmesini sağlamak için  
  
1. <xref:System.DateTime> nesneleri oluşturun.  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2. <xref:System.Windows.Forms.MonthCalendar> denetiminin <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>veya <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> yöntemini çağırarak tek bir tarih kalın yapın.  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     –veya–  
  
     <xref:System.DateTime> nesnelerden oluşan bir dizi oluşturarak ve bunu özelliklerden birine atayarak, her bir tarih kümesini her bir kez kalın yapın.  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Düzenli yazı tipinde bir tarih görünmesini sağlamak için  
  
1. <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>veya <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> yöntemini çağırarak normal yazı tipinde tek bir kalın tarih görünür hale getirin.  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     –veya–  
  
     <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>veya <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metodunu çağırarak, üç listelerden birindeki tüm kalın tarihleri kaldırın.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> yöntemini çağırarak yazı tipinin görünümünü güncelleştirin.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme](how-to-change-monthcalendar-control-appearance.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme](display-more-than-one-month-wf-monthcalendar-control.md)
