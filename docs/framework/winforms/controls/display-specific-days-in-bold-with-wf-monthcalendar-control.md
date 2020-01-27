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
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="2c759-102">Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2c759-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="2c759-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi günleri, tek tarihler veya tekrarlayan bir şekilde kalın türde gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="2c759-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="2c759-104">Bu işlem, tatiller ve hafta sonları gibi özel tarihlere dikkat çekmek için yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c759-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="2c759-105">Üç özellik bu özelliği denetler.</span><span class="sxs-lookup"><span data-stu-id="2c759-105">Three properties control this feature.</span></span> <span data-ttu-id="2c759-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> özelliği tek tarihleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2c759-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="2c759-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> özelliği, her yıl kalın olarak görünen tarihleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2c759-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="2c759-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> özelliği, her ay kalın olarak görünen tarihleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2c759-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="2c759-109">Bu özelliklerin her biri, <xref:System.DateTime> nesnelerden oluşan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="2c759-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="2c759-110">Bu listelerden birini bir tarih eklemek veya kaldırmak için <xref:System.DateTime> nesnesi eklemeniz veya kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c759-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="2c759-111">Bir tarihin kalın türde görünmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="2c759-111">To make a date appear in bold type</span></span>  
  
1. <span data-ttu-id="2c759-112"><xref:System.DateTime> nesneleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c759-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2. <span data-ttu-id="2c759-113"><xref:System.Windows.Forms.MonthCalendar> denetiminin <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>veya <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> yöntemini çağırarak tek bir tarih kalın yapın.</span><span class="sxs-lookup"><span data-stu-id="2c759-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="2c759-114">–veya–</span><span class="sxs-lookup"><span data-stu-id="2c759-114">–or–</span></span>  
  
     <span data-ttu-id="2c759-115"><xref:System.DateTime> nesnelerden oluşan bir dizi oluşturarak ve bunu özelliklerden birine atayarak, her bir tarih kümesini her bir kez kalın yapın.</span><span class="sxs-lookup"><span data-stu-id="2c759-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="2c759-116">Düzenli yazı tipinde bir tarih görünmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="2c759-116">To make a date appear in the regular font</span></span>  
  
1. <span data-ttu-id="2c759-117"><xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>veya <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> yöntemini çağırarak normal yazı tipinde tek bir kalın tarih görünür hale getirin.</span><span class="sxs-lookup"><span data-stu-id="2c759-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="2c759-118">–veya–</span><span class="sxs-lookup"><span data-stu-id="2c759-118">–or–</span></span>  
  
     <span data-ttu-id="2c759-119"><xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>veya <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metodunu çağırarak, üç listelerden birindeki tüm kalın tarihleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2c759-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. <span data-ttu-id="2c759-120"><xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> yöntemini çağırarak yazı tipinin görünümünü güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="2c759-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2c759-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c759-121">See also</span></span>

- [<span data-ttu-id="2c759-122">MonthCalendar Denetimi</span><span class="sxs-lookup"><span data-stu-id="2c759-122">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="2c759-123">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme</span><span class="sxs-lookup"><span data-stu-id="2c759-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="2c759-124">Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2c759-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="2c759-125">Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2c759-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
