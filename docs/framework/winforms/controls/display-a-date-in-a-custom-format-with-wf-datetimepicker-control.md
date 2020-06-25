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
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimi, denetimdeki tarih ve saatlerin görüntülenmesini biçimlendirme esnekliği sağlar. <xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliği, içinde listelenen önceden tanımlanmış biçimler arasından seçim yapmanıza olanak tanır <xref:System.Windows.Forms.DateTimePickerFormat> . Bunlardan hiçbiri amacınıza uygun değilse, içinde listelenen biçim karakterlerini kullanarak kendi biçim stilinizi oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .  
  
### <a name="to-display-a-custom-format"></a>Özel bir biçim göstermek için  
  
1. <xref:System.Windows.Forms.DateTimePicker.Format%2A>Özelliğini olarak ayarlayın `DateTimePickerFormat.Custom` .  
  
2. <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>Özelliği bir biçim dizesine ayarlayın.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Biçimli değere metin eklemek için  
  
1. "M" gibi biçim karakteri olmayan herhangi bir karakteri veya ":" gibi bir sınırlayıcıyı çevrelemek için tek tırnak işaretleri kullanın. Örneğin, aşağıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimindeki geçerli tarihi görüntüler.  
  
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
  
     Kültür ayarına bağlı olarak, tek tırnak işaretleri içine alınmış karakterler değiştirilebilir. Örneğin, yukarıdaki biçim dizesi Ingilizce (Birleşik Devletler) kültürünün "Bugün: 05:30:31 Cuma Mart 02, 2012" biçimiyle geçerli tarihi görüntüler. İlk iki nokta, "hh: mm: ss" içinde olduğu gibi bir sınırlandırma karakteri olması amaçlanmadığı için tek tırnak işaretleri içine alınmıştır. Başka bir kültürde, biçim "Bugün: 05.30.31 Cuma ve 02 Mart 2012" olarak görünebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DateTimePicker Denetimi](datetimepicker-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
