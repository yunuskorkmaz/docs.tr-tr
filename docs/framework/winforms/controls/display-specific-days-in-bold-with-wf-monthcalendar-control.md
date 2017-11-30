---
title: "Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18a199592a8bfbef2e4a15b056e37af6d885f5f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetim görüntüleyebilir günleri kalın yazıyla tekil tarihleri veya yinelenen aralıklarla. Dikkat çekmek tatiller ve hafta sonları gibi özel tarihler için bunu yapabilirsiniz.  
  
 Bu özellik üç özellikleri denetler. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Özelliği, tek tarihleri içerir. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Özelliği her yıl kalın görüntülenen tarihler içerir. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Özelliği, her ay kalın görüntülenen tarihler içerir. Bu özelliklerin her biri bir dizi içeren <xref:System.DateTime> nesneleri. Eklemek veya bu listelerden birine bir tarih kaldırmak için ekleyebilir veya kaldırabilirsiniz bir <xref:System.DateTime> nesnesi.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Bir tarih kalın olarak görünür yapmak için  
  
1.  Oluşturma <xref:System.DateTime> nesneleri.  
  
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
  
2.  Tek bir tarihi çağırarak kalın yapın <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, veya <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> yöntemi <xref:System.Windows.Forms.MonthCalendar> denetim.  
  
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
  
     – veya –  
  
     Tarih kümesini kalın tümünü bir defada bir dizi oluşturarak <xref:System.DateTime> nesneleri ve özellikleri birine atama.  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Bir tarih normal yazı tipini görünür yapmak için  
  
1.  Bir tek kalın tarihi çağırarak normal yazı tipini görünür hale <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, veya <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> yöntemi.  
  
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
  
     – veya –  
  
     Tüm Kalın tarihleri üç listeleri birinden çağırarak kaldırın <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, veya <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> yöntemi.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  Yazı tipi görünümünü çağırarak güncelleştirme <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> yöntemi.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MonthCalendar denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
