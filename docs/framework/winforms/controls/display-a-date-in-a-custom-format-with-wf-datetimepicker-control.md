---
title: 'Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme'
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
ms.openlocfilehash: 0c454580c6f3aa1fadb6e98d2ee715da948364b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192998"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="70f54-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="70f54-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="70f54-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetim görüntülenmesini tarihler ve saatler denetiminde biçimlendirme esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="70f54-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="70f54-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Özellik listelenen önceden tanımlanmış biçimlerinden seçmenize olanak tanır <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="70f54-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="70f54-105">Bunlardan hiçbiri amaçlarınız için yeterli ise, listelenen biçim karakterleri kullanarak kendi biçim stilini oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="70f54-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="70f54-106">Özel bir biçim görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="70f54-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="70f54-107">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğini `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="70f54-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="70f54-108">Ayarlama <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğini bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="70f54-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="70f54-109">Biçimlendirilmiş değer metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="70f54-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="70f54-110">"M" gibi bir biçim karakteri veya bir sınırlayıcı gibi herhangi bir karakterle kapsamak için tek tırnak işaretleri kullanın ":".</span><span class="sxs-lookup"><span data-stu-id="70f54-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="70f54-111">Örneğin, aşağıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 Mart Cuma 02, 2012" İngilizce (ABD) kültürünün içinde.</span><span class="sxs-lookup"><span data-stu-id="70f54-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="70f54-112">Kültür ayarı bağlı olarak, tek tırnak işaretleri arasına değil herhangi bir karakter değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="70f54-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="70f54-113">Örneğin, yukarıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 Mart Cuma 02, 2012" İngilizce (ABD) kültürünün içinde.</span><span class="sxs-lookup"><span data-stu-id="70f54-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="70f54-114">"Ss" içinde olduğu gibi bir sınırlayıcı karakter olacak şekilde tasarlanmamıştır, çünkü ilk iki nokta üst üste tek tırnak içine alınmış unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70f54-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="70f54-115">Başka bir kültürün biçimi olarak görünür "Bugün: 05.30.31 Friday March 02, 2012".</span><span class="sxs-lookup"><span data-stu-id="70f54-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f54-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70f54-116">See also</span></span>

- [<span data-ttu-id="70f54-117">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="70f54-117">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="70f54-118">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="70f54-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
