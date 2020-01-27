---
title: MonthCalendar denetiminde birden fazla ay görüntüleme
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
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745891"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="0c57f-102">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0c57f-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="0c57f-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi, her seferinde 12 aya kadar gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0c57f-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="0c57f-104">Varsayılan olarak, denetim yalnızca bir ay görüntüler, ancak kaç ay görüntülendiğini ve denetimin içinde nasıl düzenlendiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c57f-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="0c57f-105">Takvim boyutlarını değiştirdiğinizde denetim yeniden boyutlandırılır, bu nedenle formda yeni boyutlar için yeterli yer olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0c57f-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="0c57f-106">Birden çok ay görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0c57f-106">To display multiple months</span></span>  
  
- <span data-ttu-id="0c57f-107"><xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> özelliğini yatay ve dikey olarak görüntülenecek ay sayısı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0c57f-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0c57f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c57f-108">See also</span></span>

- [<span data-ttu-id="0c57f-109">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="0c57f-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="0c57f-110">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme</span><span class="sxs-lookup"><span data-stu-id="0c57f-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="0c57f-111">Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0c57f-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
