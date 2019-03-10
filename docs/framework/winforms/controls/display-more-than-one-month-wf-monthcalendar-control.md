---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: febed820bae460f51bb19f08caa6027011abd55d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715353"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="77453-102">Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme</span><span class="sxs-lookup"><span data-stu-id="77453-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="77453-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi, aynı anda en fazla 12 ay görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77453-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="77453-104">Varsayılan olarak, yalnızca bir ay denetim görüntüler, ancak kaç ay görüntülenir ve içindeki denetim nasıl düzenlenir belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77453-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="77453-105">Takvim boyutları değiştirdiğinizde, denetimi yeniden boyutlandırıldı, bu nedenle yeni boyutlar için formda yetecek kadar yer olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="77453-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="77453-106">Birden çok aya görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="77453-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="77453-107">Ayarlama <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliğini yatay ve dikey olarak görüntülenecek ay sayısı.</span><span class="sxs-lookup"><span data-stu-id="77453-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77453-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77453-108">See also</span></span>
- [<span data-ttu-id="77453-109">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="77453-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="77453-110">Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin</span><span class="sxs-lookup"><span data-stu-id="77453-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="77453-111">Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="77453-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
