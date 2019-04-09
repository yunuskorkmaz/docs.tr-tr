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
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetim görüntülenmesini tarihler ve saatler denetiminde biçimlendirme esneklik sağlar. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Özellik listelenen önceden tanımlanmış biçimlerinden seçmenize olanak tanır <xref:System.Windows.Forms.DateTimePickerFormat>. Bunlardan hiçbiri amaçlarınız için yeterli ise, listelenen biçim karakterleri kullanarak kendi biçim stilini oluşturabilirsiniz <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Özel bir biçim görüntülemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.DateTimePicker.Format%2A> özelliğini `DateTimePickerFormat.Custom`.  
  
2.  Ayarlama <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> özelliğini bir biçim dizesi.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Biçimlendirilmiş değer metin eklemek için  
  
1.  "M" gibi bir biçim karakteri veya bir sınırlayıcı gibi herhangi bir karakterle kapsamak için tek tırnak işaretleri kullanın ":". Örneğin, aşağıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 Mart Cuma 02, 2012" İngilizce (ABD) kültürünün içinde.  
  
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
  
     Kültür ayarı bağlı olarak, tek tırnak işaretleri arasına değil herhangi bir karakter değiştirilebilir. Örneğin, yukarıdaki biçim dizesi biçiminde geçerli tarihi görüntüler "Bugün: 05:30:31 Mart Cuma 02, 2012" İngilizce (ABD) kültürünün içinde. "Ss" içinde olduğu gibi bir sınırlayıcı karakter olacak şekilde tasarlanmamıştır, çünkü ilk iki nokta üst üste tek tırnak içine alınmış unutmayın. Başka bir kültürün biçimi olarak görünür "Bugün: 05.30.31 Friday March 02, 2012".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DateTimePicker Denetimi](datetimepicker-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
