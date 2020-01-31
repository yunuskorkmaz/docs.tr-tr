---
title: DateTimePicker denetimi ile ayarlama ve dönüş tarihleri
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
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747104"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme
Windows Forms <xref:System.Windows.Forms.DateTimePicker> denetimindeki Şu anda seçili olan tarih veya saat <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği tarafından belirlenir. Denetim görüntülenmeden önce <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğini ayarlayabilirsiniz (örneğin tasarım zamanı veya formun <xref:System.Windows.Forms.Form.Load> olayında), başlangıçta hangi tarihin seçileceğini belirleyin. Varsayılan olarak, denetimin <xref:System.Windows.Forms.DateTimePicker.Value%2A> geçerli tarih olarak ayarlanır. Kodda <xref:System.Windows.Forms.DateTimePicker.Value%2A> denetimin değiştirirseniz, denetim yeni ayarı yansıtmak için form üzerinde otomatik olarak güncelleştirilir.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği, değeri olarak bir <xref:System.DateTime> yapısı döndürür. <xref:System.DateTime> yapısının görüntülenen tarihle ilgili belirli bilgileri döndüren birkaç özelliği vardır. Bu özellikler yalnızca bir değer döndürmek için kullanılabilir; Bu değerleri bir değer ayarlamak için kullanmayın.  
  
- Tarih değerleri için <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>ve <xref:System.DateTime.Year%2A> özellikleri seçili tarihin bu zaman birimleri için tamsayı değerler döndürür. <xref:System.DateTime.DayOfWeek%2A> özelliği, haftanın seçili gününü gösteren bir değer döndürür (olası değerler <xref:System.DayOfWeek> numaralandırmada listelenmiştir).  
  
- Zaman değerleri için <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>ve <xref:System.DateTime.Millisecond%2A> özellikleri bu zaman birimleri için tamsayı değerler döndürür. Denetimi saatleri görüntüleyecek şekilde yapılandırmak için bkz. [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Denetimin tarih ve saat değerini ayarlamak için  
  
- <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğini bir tarih veya saat değeri olarak ayarlayın.  
  
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
  
- Tüm değeri denetimde biçimlendirilen şekilde döndürmek için <xref:System.Windows.Forms.DateTimePicker.Text%2A> özelliğini çağırın veya değerin bir kısmını döndürmek için <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliğinin uygun yöntemini çağırın. Bilgileri kullanıcıya görüntülenebilen bir dizeye dönüştürmek için <xref:System.Windows.Forms.DateTimePicker.ToString%2A> kullanın.  
  
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
