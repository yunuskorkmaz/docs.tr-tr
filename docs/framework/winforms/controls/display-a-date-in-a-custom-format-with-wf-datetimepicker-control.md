---
title: DateTimePicker denetimi ile özel biçimde bir tarih görüntüleme
description: Denetimdeki tarih ve saatlerin görüntülenmesini biçimlendirmek için Windows Forms DateTimePicker denetimini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325837"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="851d3-103">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="851d3-103">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="851d3-104">Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimi, denetimdeki tarih ve saatlerin görüntülenmesini biçimlendirme esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="851d3-104">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="851d3-105"><xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliği, içinde listelenen önceden tanımlanmış biçimler arasından seçim yapmanıza olanak tanır <xref:System.Windows.Forms.DateTimePickerFormat> .</span><span class="sxs-lookup"><span data-stu-id="851d3-105">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="851d3-106">Bunlardan hiçbiri amacınıza uygun değilse, içinde listelenen biçim karakterlerini kullanarak kendi biçim stilinizi oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .</span><span class="sxs-lookup"><span data-stu-id="851d3-106">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="851d3-107">Özel bir biçim göstermek için</span><span class="sxs-lookup"><span data-stu-id="851d3-107">To display a custom format</span></span>  
  
1. <span data-ttu-id="851d3-108"><xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliğini olarak ayarlayın `DateTimePickerFormat.Custom` .</span><span class="sxs-lookup"><span data-stu-id="851d3-108">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="851d3-109"><xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>Özelliği bir biçim dizesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="851d3-109">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="851d3-110">Biçimli değere metin eklemek için</span><span class="sxs-lookup"><span data-stu-id="851d3-110">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="851d3-111">"M" gibi biçim karakteri olmayan herhangi bir karakteri veya ":" gibi bir sınırlayıcıyı çevrelemek için tek tırnak işaretleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="851d3-111">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="851d3-112">Örneğin, aşağıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimindeki geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="851d3-112">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="851d3-113">Kültür ayarına bağlı olarak, tek tırnak işaretleri içine alınmış karakterler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="851d3-113">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="851d3-114">Örneğin, yukarıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimiyle geçerli tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="851d3-114">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="851d3-115">İlk iki nokta, "hh: mm: ss" içinde olduğu gibi bir sınırlandırma karakteri olması amaçlanmadığı için tek tırnak işaretleri içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="851d3-115">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="851d3-116">Başka bir kültürde, biçim "Bugün: 05.30.31 Cuma ve 02 Mart 2012" olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="851d3-116">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="851d3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="851d3-117">See also</span></span>

- [<span data-ttu-id="851d3-118">DateTimePicker Denetimi</span><span class="sxs-lookup"><span data-stu-id="851d3-118">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="851d3-119">Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="851d3-119">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
