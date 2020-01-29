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
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="c6741-102">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde tarih aralığı seçme</span><span class="sxs-lookup"><span data-stu-id="c6741-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="c6741-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetiminin önemli bir özelliği, kullanıcının bir tarih aralığı seçmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c6741-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="c6741-104">Bu özellik, yalnızca kullanıcının tek bir tarih/saat değeri seçmesini sağlayan <xref:System.Windows.Forms.DateTimePicker> denetiminin tarih seçimi özelliğinin bir geliştirmedir.</span><span class="sxs-lookup"><span data-stu-id="c6741-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="c6741-105"><xref:System.Windows.Forms.MonthCalendar> denetiminin özelliklerini kullanarak bir tarih aralığı ayarlayabilir veya Kullanıcı tarafından ayarlanmış bir seçim aralığı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6741-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="c6741-106">Aşağıdaki kod örneğinde, bir seçim aralığının nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6741-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="c6741-107">Bir tarih aralığı seçmek için</span><span class="sxs-lookup"><span data-stu-id="c6741-107">To select a range of dates</span></span>  
  
1. <span data-ttu-id="c6741-108">Bir aralıktaki ilk ve son tarihleri temsil eden <xref:System.DateTime> nesneleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6741-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2. <span data-ttu-id="c6741-109"><xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6741-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="c6741-110">–veya–</span><span class="sxs-lookup"><span data-stu-id="c6741-110">–or–</span></span>  
  
     <span data-ttu-id="c6741-111"><xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> ve <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6741-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6741-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6741-112">See also</span></span>

- [<span data-ttu-id="c6741-113">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="c6741-113">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="c6741-114">Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c6741-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="c6741-115">Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c6741-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="c6741-116">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c6741-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
