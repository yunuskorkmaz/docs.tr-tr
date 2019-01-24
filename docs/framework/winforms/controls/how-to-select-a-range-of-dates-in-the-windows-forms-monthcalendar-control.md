---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin'
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
ms.openlocfilehash: 4c7100f77c313d219cfd4cceff5ae3015eae4c18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558455"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="2352a-102">Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin</span><span class="sxs-lookup"><span data-stu-id="2352a-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="2352a-103">Windows Forms ve önemli bir özelliği <xref:System.Windows.Forms.MonthCalendar> denetimi, kullanıcının bir tarih aralığını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2352a-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="2352a-104">Bu özellik bir geliştirme Tarih Seçimi özelliğidir <xref:System.Windows.Forms.DateTimePicker> denetimi, yalnızca tek bir tarih/saat değeri seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2352a-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="2352a-105">Tarih aralığı ayarlayın veya alın özelliklerini kullanarak kullanıcı tarafından ayarlanan bir seçim aralığını <xref:System.Windows.Forms.MonthCalendar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2352a-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="2352a-106">Aşağıdaki kod örneği, bir seçim aralığını ayarlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2352a-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="2352a-107">Tarih aralığı seçin</span><span class="sxs-lookup"><span data-stu-id="2352a-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="2352a-108">Oluşturma <xref:System.DateTime> bir aralıktaki ilk ve son tarihleri temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2352a-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="2352a-109">Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2352a-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="2352a-110">– veya –</span><span class="sxs-lookup"><span data-stu-id="2352a-110">–or–</span></span>  
  
     <span data-ttu-id="2352a-111">Ayarlama <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> ve <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2352a-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2352a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2352a-112">See also</span></span>
- [<span data-ttu-id="2352a-113">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="2352a-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="2352a-114">Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="2352a-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="2352a-115">Nasıl yapılır: Windows ile belirli günleri kalın olarak görüntüleme Forms MonthCalendar denetimi</span><span class="sxs-lookup"><span data-stu-id="2352a-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="2352a-116">Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2352a-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
