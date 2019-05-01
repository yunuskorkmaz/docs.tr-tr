---
title: 'Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme'
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
ms.openlocfilehash: cc4f0bdf7355cda61e6cb95f5e0b18c4f83aa62b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013354"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme
Seçili tarih veya saat Windows Forms'ta <xref:System.Windows.Forms.DateTimePicker> denetimi tarafından belirlenir <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği. Ayarlayabileceğiniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> denetim görüntülenmeden önce özelliği (örneğin, tasarım zamanında ya da formun <xref:System.Windows.Forms.Form.Load> olay) hangi tarih denetiminde başlangıçta seçilir belirlemek için. Varsayılan olarak, denetime ait <xref:System.Windows.Forms.DateTimePicker.Value%2A> geçerli tarihe ayarlama. Denetimin değiştirirseniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> kodda denetimi form üzerinde yeni ayarını yansıtacak şekilde otomatik olarak güncelleştirilir.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Özelliği döndürür bir <xref:System.DateTime> yapısı olarak değeri. Çeşitli özellikleri vardır <xref:System.DateTime> görüntülenen tarih hakkında belirli bilgi döndüren yapısı. Bu özellikler, yalnızca bir değer döndürmek için kullanılabilir; bunları bir değer ayarlamak için kullanmayın.  
  
- Tarih değerlerinin <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, ve <xref:System.DateTime.Year%2A> özellikleri, seçilen tarihten için bu zaman birimlerini tamsayı değerleri döndürür. <xref:System.DateTime.DayOfWeek%2A> Özelliği seçili haftanın gününü gösteren bir değeri döndürür (olası değerler listelenmiştir <xref:System.DayOfWeek> sabit listesi).  
  
- Saat değerleri için <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, ve <xref:System.DateTime.Millisecond%2A> özellikleri, o zaman birimleri için tamsayı değerleri döndürür. Sürelerini görüntülemek için denetimi yapılandırmak için bkz [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Denetimin tarih ve saat değerini ayarlamak için  
  
- Ayarlama <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği bir tarih veya saat değeri.  
  
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
  
- Çağrı <xref:System.Windows.Forms.DateTimePicker.Text%2A> denetiminde biçimlendirilmiş değerin tamamını döndürür ya da uygun yöntemini çağırmak için özellik <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği değerinin bir bölümünü döndürür. Kullanım <xref:System.Windows.Forms.DateTimePicker.ToString%2A> bilgileri kullanıcıya görüntülenen bir dizeye dönüştürmek için.  
  
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
- [Nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
