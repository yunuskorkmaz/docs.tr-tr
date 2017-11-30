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
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="f1830-102">Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f1830-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="f1830-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetim görüntüleyebilir günleri kalın yazıyla tekil tarihleri veya yinelenen aralıklarla.</span><span class="sxs-lookup"><span data-stu-id="f1830-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="f1830-104">Dikkat çekmek tatiller ve hafta sonları gibi özel tarihler için bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1830-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="f1830-105">Bu özellik üç özellikleri denetler.</span><span class="sxs-lookup"><span data-stu-id="f1830-105">Three properties control this feature.</span></span> <span data-ttu-id="f1830-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Özelliği, tek tarihleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1830-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="f1830-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Özelliği her yıl kalın görüntülenen tarihler içerir.</span><span class="sxs-lookup"><span data-stu-id="f1830-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="f1830-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Özelliği, her ay kalın görüntülenen tarihler içerir.</span><span class="sxs-lookup"><span data-stu-id="f1830-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="f1830-109">Bu özelliklerin her biri bir dizi içeren <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f1830-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="f1830-110">Eklemek veya bu listelerden birine bir tarih kaldırmak için ekleyebilir veya kaldırabilirsiniz bir <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f1830-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="f1830-111">Bir tarih kalın olarak görünür yapmak için</span><span class="sxs-lookup"><span data-stu-id="f1830-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="f1830-112">Oluşturma <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f1830-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="f1830-113">Tek bir tarihi çağırarak kalın yapın <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, veya <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> yöntemi <xref:System.Windows.Forms.MonthCalendar> denetim.</span><span class="sxs-lookup"><span data-stu-id="f1830-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="f1830-114">– veya –</span><span class="sxs-lookup"><span data-stu-id="f1830-114">–or–</span></span>  
  
     <span data-ttu-id="f1830-115">Tarih kümesini kalın tümünü bir defada bir dizi oluşturarak <xref:System.DateTime> nesneleri ve özellikleri birine atama.</span><span class="sxs-lookup"><span data-stu-id="f1830-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="f1830-116">Bir tarih normal yazı tipini görünür yapmak için</span><span class="sxs-lookup"><span data-stu-id="f1830-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="f1830-117">Bir tek kalın tarihi çağırarak normal yazı tipini görünür hale <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, veya <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1830-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="f1830-118">– veya –</span><span class="sxs-lookup"><span data-stu-id="f1830-118">–or–</span></span>  
  
     <span data-ttu-id="f1830-119">Tüm Kalın tarihleri üç listeleri birinden çağırarak kaldırın <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, veya <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1830-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="f1830-120">Yazı tipi görünümünü çağırarak güncelleştirme <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1830-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1830-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1830-121">See Also</span></span>  
 [<span data-ttu-id="f1830-122">MonthCalendar denetimi</span><span class="sxs-lookup"><span data-stu-id="f1830-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="f1830-123">Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin</span><span class="sxs-lookup"><span data-stu-id="f1830-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="f1830-124">Nasıl yapılır: Windows Forms MonthCalendar denetiminin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="f1830-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="f1830-125">Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f1830-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
