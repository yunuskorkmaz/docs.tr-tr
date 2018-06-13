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
ms.openlocfilehash: 2f563b5de9b80dab2af00290e8a6b3b309410a9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526015"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetim tarihler ve saatler denetiminde görüntüsünü biçimlendirme esneklik sağlar. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Özelliği listelenen önceden tanımlanmış biçimlerden seçmenize olanak verir <xref:System.Windows.Forms.DateTimePickerFormat>. Bunlar hiçbiri amaçlarınız için yeterli değilse listelenen biçimi karakter kullanarak kendi biçimi stili oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Özel bir biçim görüntülemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğine `DateTimePickerFormat.Custom`.  
  
2.  Ayarlama <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğine bir biçim dizesi.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Biçimlendirilmiş değer bir metin eklemek için  
  
1.  Tek tırnak işareti "M" gibi bir biçim karakter veya bir sınırlayıcı gibi herhangi bir karakter tırnak içine alın ":". Örneğin, aşağıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 02 Mart 2012 Cuma" İngilizce (ABD) kültür.  
  
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
  
     Kültür ayarı bağlı olarak, tek tırnak işaretleri içine olmayan herhangi bir karakter değiştirilebilir. Örneğin, yukarıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 02 Mart 2012 Cuma" İngilizce (ABD) kültür. "Ss: dd: içinde" olduğu gibi sınırlandırma karakterine olacak şekilde tasarlanmamıştır çünkü ilk iki nokta üst üste tek tırnak içine alınmış olduğunu unutmayın. Başka bir kültürün biçimi olarak görünebilir "Bugün: 05.30.31 02 Mart 2012 Cuma".  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DateTimePicker Denetimi](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
