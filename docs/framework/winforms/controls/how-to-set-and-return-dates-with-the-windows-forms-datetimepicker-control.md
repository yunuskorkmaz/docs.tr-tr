---
title: "Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme"
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
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4df12d196c02b1d868d395a10ca17abafaa0fb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="c86ad-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="c86ad-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="c86ad-103">Şu anda seçili tarih veya saat Windows Forms'ta <xref:System.Windows.Forms.DateTimePicker> denetim belirlenir <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c86ad-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="c86ad-104">Ayarlayabileceğiniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> denetimi görüntülenmeden önce özelliği (örneğin, tasarım zamanında veya formun <xref:System.Windows.Forms.Form.Load> olay) hangi tarih başlangıçta denetiminde seçilir belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="c86ad-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="c86ad-105">Varsayılan olarak, Denetim 's <xref:System.Windows.Forms.DateTimePicker.Value%2A> geçerli tarih olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c86ad-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="c86ad-106">Denetimin değiştirirseniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> kodda denetimi yeni ayar yansıtmak için form üzerinde otomatik olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c86ad-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="c86ad-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> Özelliği döndürür bir <xref:System.DateTime> yapısı değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="c86ad-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="c86ad-108">Çeşitli özellikleri vardır <xref:System.DateTime> görüntülenen tarih hakkındaki belirli bilgileri döndürmek yapısı.</span><span class="sxs-lookup"><span data-stu-id="c86ad-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="c86ad-109">Bu özellikler, yalnızca bir değer döndürmek için kullanılabilir; bunları bir değer ayarlamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c86ad-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="c86ad-110">Tarih değerleri için <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, ve <xref:System.DateTime.Year%2A> özellikleri, seçilen tarihten bu zaman birimleri için tamsayı değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86ad-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="c86ad-111"><xref:System.DateTime.DayOfWeek%2A> Özelliği seçili haftanın gününü gösteren bir değeri döndürür (olası değerler olarak listelenen <xref:System.DayOfWeek> numaralandırması).</span><span class="sxs-lookup"><span data-stu-id="c86ad-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="c86ad-112">Saat değerleri için <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, ve <xref:System.DateTime.Millisecond%2A> özellikleri için bu zaman birimlerini tamsayı değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86ad-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="c86ad-113">Sürelerini görüntülemek için denetimi yapılandırmak için bkz: [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="c86ad-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="c86ad-114">Denetimin tarih ve saat değeri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c86ad-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="c86ad-115">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Value%2A> bir tarih veya saat değeri özelliğine.</span><span class="sxs-lookup"><span data-stu-id="c86ad-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="c86ad-116">Tarih ve saat değeri döndürmek için</span><span class="sxs-lookup"><span data-stu-id="c86ad-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="c86ad-117">Çağrı <xref:System.Windows.Forms.DateTimePicker.Text%2A> denetiminde biçimli olarak tüm değerini döndürür veya uygun yöntemini çağırmak için özellik <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği değerinin bir bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="c86ad-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="c86ad-118">Kullanım <xref:System.Windows.Forms.DateTimePicker.ToString%2A> bilgileri kullanıcıya görüntülenen bir dizeye dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="c86ad-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c86ad-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c86ad-119">See Also</span></span>  
 [<span data-ttu-id="c86ad-120">DateTimePicker denetimi</span><span class="sxs-lookup"><span data-stu-id="c86ad-120">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="c86ad-121">Nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c86ad-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
