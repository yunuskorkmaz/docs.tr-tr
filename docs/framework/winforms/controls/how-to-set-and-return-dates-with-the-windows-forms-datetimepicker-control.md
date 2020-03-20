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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetiminde şu anda seçili <xref:System.Windows.Forms.DateTimePicker.Value%2A> tarih veya saat özellik tarafından belirlenir. Denetimde ilk <xref:System.Windows.Forms.DateTimePicker.Value%2A> olarak hangi tarihin seçileceğini belirlemek için özelliği denetim <xref:System.Windows.Forms.Form.Load> görüntülenmeden önce (örneğin, tasarım zamanında veya formun olayında) ayarlayabilirsiniz. Varsayılan olarak, denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> durumu geçerli tarihe ayarlanır. Denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> koddaki ni değiştirirseniz, denetim yeni ayarı yansıtacak şekilde formda otomatik olarak güncelleştirilir.  
  
 Özellik <xref:System.Windows.Forms.DateTimePicker.Value%2A> değeri <xref:System.DateTime> olarak bir yapı döndürür. Yapının <xref:System.DateTime> görüntülenen tarih hakkında belirli bilgileri döndüren birkaç özelliği vardır. Bu özellikler yalnızca bir değeri döndürmek için kullanılabilir; bir değer belirlemek için kullanmayın.  
  
- Tarih değerleri <xref:System.DateTime.Month%2A>için, <xref:System.DateTime.Day%2A>, <xref:System.DateTime.Year%2A> ve özellikleri seçilen tarihin bu zaman birimleri için yokometre değerlerini döndürür. Özellik, <xref:System.DateTime.DayOfWeek%2A> haftanın seçili gününü gösteren bir değer döndürür <xref:System.DayOfWeek> (olası değerler numaralandırmada listelenir).  
  
- <xref:System.DateTime.Hour%2A>Zaman değerleri için, <xref:System.DateTime.Minute%2A> <xref:System.DateTime.Second%2A>, <xref:System.DateTime.Millisecond%2A> , , ve özellikleri bu zaman birimleri için yokometre değerlerini döndürür. Denetimi görüntüleme sürelerine yapılandırmak için [bkz.](how-to-display-time-with-the-datetimepicker-control.md)  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Denetimin tarih ve saat değerini ayarlamak için  
  
- Özelliği <xref:System.Windows.Forms.DateTimePicker.Value%2A> bir tarih veya saat değerine ayarlayın.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Tarih ve saat değerini döndürmek için  
  
- Denetimde <xref:System.Windows.Forms.DateTimePicker.Text%2A> biçimlendirilmiş tüm değeri döndürmek için özelliği çağırın veya değerin bir bölümünü döndürmek için özelliğin <xref:System.Windows.Forms.DateTimePicker.Value%2A> uygun yöntemini çağırın. Bilgileri <xref:System.Windows.Forms.DateTimePicker.ToString%2A> kullanıcıya görüntülenebilecek bir dize dönüştürmeyi kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DateTimePicker Denetimi](datetimepicker-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Özel Biçimde Tarih Görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
