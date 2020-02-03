---
title: DateTimePicker denetimi ile özel biçimde bir tarih görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745939"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="d58eb-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d58eb-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="d58eb-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimi, denetimdeki tarih ve saatlerin görüntülenmesini biçimlendirme esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d58eb-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="d58eb-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliği, <xref:System.Windows.Forms.DateTimePickerFormat>listelenen önceden tanımlanmış biçimler arasından seçim yapmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d58eb-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="d58eb-105">Bunlardan hiçbiri amacınıza uygun değilse, <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>listelenen biçim karakterlerini kullanarak kendi biçim stilinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d58eb-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="d58eb-106">Özel bir biçim göstermek için</span><span class="sxs-lookup"><span data-stu-id="d58eb-106">To display a custom format</span></span>  
  
1. <span data-ttu-id="d58eb-107"><xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğini `DateTimePickerFormat.Custom`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d58eb-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="d58eb-108"><xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğini bir biçim dizesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d58eb-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="d58eb-109">Biçimli değere metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="d58eb-109">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="d58eb-110">"M" gibi biçim karakteri olmayan herhangi bir karakteri veya ":" gibi bir sınırlayıcıyı çevrelemek için tek tırnak işaretleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d58eb-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="d58eb-111">Örneğin, aşağıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimindeki geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d58eb-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="d58eb-112">Kültür ayarına bağlı olarak, tek tırnak işaretleri içine alınmış karakterler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d58eb-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="d58eb-113">Örneğin, yukarıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimiyle geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d58eb-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="d58eb-114">İlk iki nokta, "hh: mm: ss" içinde olduğu gibi bir sınırlandırma karakteri olması amaçlanmadığı için tek tırnak işaretleri içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d58eb-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="d58eb-115">Başka bir kültürde, biçim "Bugün: 05.30.31 Cuma ve 02 Mart 2012" olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="d58eb-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58eb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d58eb-116">See also</span></span>

- [<span data-ttu-id="d58eb-117">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="d58eb-117">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="d58eb-118">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="d58eb-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
