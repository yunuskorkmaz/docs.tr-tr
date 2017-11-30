---
title: "Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme"
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
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="37816-102">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="37816-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="37816-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetim tarihler ve saatler denetiminde görüntüsünü biçimlendirme esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="37816-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="37816-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Özelliği listelenen önceden tanımlanmış biçimlerden seçmenize olanak verir <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="37816-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="37816-105">Bunlar hiçbiri amaçlarınız için yeterli değilse listelenen biçimi karakter kullanarak kendi biçimi stili oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="37816-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="37816-106">Özel bir biçim görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="37816-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="37816-107">Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğine `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="37816-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="37816-108">Ayarlama <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğine bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="37816-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="37816-109">Biçimlendirilmiş değer bir metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="37816-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="37816-110">Tek tırnak işareti "M" gibi bir biçim karakter veya bir sınırlayıcı gibi herhangi bir karakter tırnak içine alın ":".</span><span class="sxs-lookup"><span data-stu-id="37816-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="37816-111">Örneğin, aşağıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 02 Mart 2012 Cuma" İngilizce (ABD) kültür.</span><span class="sxs-lookup"><span data-stu-id="37816-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="37816-112">Kültür ayarı bağlı olarak, tek tırnak işaretleri içine olmayan herhangi bir karakter değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="37816-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="37816-113">Örneğin, yukarıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 02 Mart 2012 Cuma" İngilizce (ABD) kültür.</span><span class="sxs-lookup"><span data-stu-id="37816-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="37816-114">"Ss: dd: içinde" olduğu gibi sınırlandırma karakterine olacak şekilde tasarlanmamıştır çünkü ilk iki nokta üst üste tek tırnak içine alınmış olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="37816-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="37816-115">Başka bir kültürün biçimi olarak görünebilir "Bugün: 05.30.31 02 Mart 2012 Cuma".</span><span class="sxs-lookup"><span data-stu-id="37816-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37816-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37816-116">See Also</span></span>  
 [<span data-ttu-id="37816-117">DateTimePicker denetimi</span><span class="sxs-lookup"><span data-stu-id="37816-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="37816-118">Nasıl yapılır: tarihleri Windows Forms DateTimePicker denetimi ayarlama ve döndürme</span><span class="sxs-lookup"><span data-stu-id="37816-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
