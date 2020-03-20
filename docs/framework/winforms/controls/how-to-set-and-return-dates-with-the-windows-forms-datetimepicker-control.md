---
title: DateTimePicker Kontrolü ile Tarihleri Ayarlama ve İade
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
ms.openlocfilehash: f958097640316715b38828e72107ab5bdb9389aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141919"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="71c04-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="71c04-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="71c04-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetiminde şu anda seçili <xref:System.Windows.Forms.DateTimePicker.Value%2A> tarih veya saat özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="71c04-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="71c04-104">Denetimde ilk <xref:System.Windows.Forms.DateTimePicker.Value%2A> olarak hangi tarihin seçileceğini belirlemek için özelliği denetim <xref:System.Windows.Forms.Form.Load> görüntülenmeden önce (örneğin, tasarım zamanında veya formun olayında) ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71c04-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="71c04-105">Varsayılan olarak, denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> durumu geçerli tarihe ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="71c04-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="71c04-106">Denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> koddaki ni değiştirirseniz, denetim yeni ayarı yansıtacak şekilde formda otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="71c04-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="71c04-107">Özellik <xref:System.Windows.Forms.DateTimePicker.Value%2A> değeri <xref:System.DateTime> olarak bir yapı döndürür.</span><span class="sxs-lookup"><span data-stu-id="71c04-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="71c04-108">Yapının <xref:System.DateTime> görüntülenen tarih hakkında belirli bilgileri döndüren birkaç özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="71c04-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="71c04-109">Bu özellikler yalnızca bir değeri döndürmek için kullanılabilir; bir değer belirlemek için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="71c04-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="71c04-110">Tarih değerleri <xref:System.DateTime.Month%2A>için, <xref:System.DateTime.Day%2A>, <xref:System.DateTime.Year%2A> ve özellikleri seçilen tarihin bu zaman birimleri için yokometre değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="71c04-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="71c04-111">Özellik, <xref:System.DateTime.DayOfWeek%2A> haftanın seçili gününü gösteren bir değer döndürür <xref:System.DayOfWeek> (olası değerler numaralandırmada listelenir).</span><span class="sxs-lookup"><span data-stu-id="71c04-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="71c04-112"><xref:System.DateTime.Hour%2A>Zaman değerleri için, <xref:System.DateTime.Minute%2A> <xref:System.DateTime.Second%2A>, <xref:System.DateTime.Millisecond%2A> , , ve özellikleri bu zaman birimleri için yokometre değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="71c04-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="71c04-113">Denetimi görüntüleme sürelerine yapılandırmak için [bkz.](how-to-display-time-with-the-datetimepicker-control.md)</span><span class="sxs-lookup"><span data-stu-id="71c04-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="71c04-114">Denetimin tarih ve saat değerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="71c04-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="71c04-115">Özelliği <xref:System.Windows.Forms.DateTimePicker.Value%2A> bir tarih veya saat değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71c04-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="71c04-116">Tarih ve saat değerini döndürmek için</span><span class="sxs-lookup"><span data-stu-id="71c04-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="71c04-117">Denetimde <xref:System.Windows.Forms.DateTimePicker.Text%2A> biçimlendirilmiş tüm değeri döndürmek için özelliği çağırın veya değerin bir bölümünü döndürmek için özelliğin <xref:System.Windows.Forms.DateTimePicker.Value%2A> uygun yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="71c04-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="71c04-118">Bilgileri <xref:System.Windows.Forms.DateTimePicker.ToString%2A> kullanıcıya görüntülenebilecek bir dize dönüştürmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="71c04-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71c04-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71c04-119">See also</span></span>

- [<span data-ttu-id="71c04-120">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="71c04-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="71c04-121">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="71c04-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
