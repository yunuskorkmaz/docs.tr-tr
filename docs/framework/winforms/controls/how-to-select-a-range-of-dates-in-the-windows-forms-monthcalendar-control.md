---
title: MonthCalendar Denetiminde tarih aralığı seçme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732901"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetiminde tarih aralığı seçme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetiminin önemli bir özelliği, kullanıcının bir tarih aralığı seçmesini sağlayabilir. Bu özellik, yalnızca kullanıcının tek bir tarih/saat değeri seçmesini sağlayan <xref:System.Windows.Forms.DateTimePicker> denetiminin tarih seçimi özelliğinin bir geliştirmedir. <xref:System.Windows.Forms.MonthCalendar> denetiminin özelliklerini kullanarak bir tarih aralığı ayarlayabilir veya Kullanıcı tarafından ayarlanmış bir seçim aralığı alabilirsiniz. Aşağıdaki kod örneğinde, bir seçim aralığının nasıl ayarlanacağı gösterilmektedir.  
  
### <a name="to-select-a-range-of-dates"></a>Bir tarih aralığı seçmek için  
  
1. Bir aralıktaki ilk ve son tarihleri temsil eden <xref:System.DateTime> nesneleri oluşturun.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2. <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> özelliğini ayarlayın.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     –veya–  
  
     <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> ve <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> özelliklerini ayarlayın.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme](how-to-change-monthcalendar-control-appearance.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme](display-more-than-one-month-wf-monthcalendar-control.md)
