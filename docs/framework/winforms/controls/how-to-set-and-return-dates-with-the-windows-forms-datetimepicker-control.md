---
title: DateTimePicker denetimi ile ayarlama ve dönüş tarihleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747104"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="e36ab-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="e36ab-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="e36ab-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimindeki Şu anda seçili olan tarih veya saat <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e36ab-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="e36ab-104">Denetim görüntülenmeden önce <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğini ayarlayabilirsiniz (örneğin tasarım zamanı veya formun <xref:System.Windows.Forms.Form.Load> olayında), başlangıçta hangi tarihin seçileceğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="e36ab-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="e36ab-105">Varsayılan olarak, denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> geçerli tarih olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e36ab-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="e36ab-106">Kodda <xref:System.Windows.Forms.DateTimePicker.Value%2A> denetimin değiştirirseniz, denetim yeni ayarı yansıtmak için form üzerinde otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e36ab-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="e36ab-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği, değeri olarak bir <xref:System.DateTime> yapısı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e36ab-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="e36ab-108"><xref:System.DateTime> yapısının görüntülenen tarihle ilgili belirli bilgileri döndüren birkaç özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="e36ab-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="e36ab-109">Bu özellikler yalnızca bir değer döndürmek için kullanılabilir; Bu değerleri bir değer ayarlamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e36ab-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="e36ab-110">Tarih değerleri için <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>ve <xref:System.DateTime.Year%2A> özellikleri seçili tarihin bu zaman birimleri için tamsayı değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="e36ab-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="e36ab-111"><xref:System.DateTime.DayOfWeek%2A> özelliği, haftanın seçili gününü gösteren bir değer döndürür (olası değerler <xref:System.DayOfWeek> numaralandırmada listelenmiştir).</span><span class="sxs-lookup"><span data-stu-id="e36ab-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="e36ab-112">Zaman değerleri için <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>ve <xref:System.DateTime.Millisecond%2A> özellikleri bu zaman birimleri için tamsayı değerler döndürür.</span><span class="sxs-lookup"><span data-stu-id="e36ab-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="e36ab-113">Denetimi saatleri görüntüleyecek şekilde yapılandırmak için bkz. [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="e36ab-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="e36ab-114">Denetimin tarih ve saat değerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e36ab-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="e36ab-115"><xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğini bir tarih veya saat değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e36ab-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="e36ab-116">Tarih ve saat değerini döndürmek için</span><span class="sxs-lookup"><span data-stu-id="e36ab-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="e36ab-117">Tüm değeri denetimde biçimlendirilen şekilde döndürmek için <xref:System.Windows.Forms.DateTimePicker.Text%2A> özelliğini çağırın veya değerin bir kısmını döndürmek için <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğinin uygun yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e36ab-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="e36ab-118">Bilgileri kullanıcıya görüntülenebilen bir dizeye dönüştürmek için <xref:System.Windows.Forms.DateTimePicker.ToString%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="e36ab-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e36ab-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e36ab-119">See also</span></span>

- [<span data-ttu-id="e36ab-120">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="e36ab-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="e36ab-121">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e36ab-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
