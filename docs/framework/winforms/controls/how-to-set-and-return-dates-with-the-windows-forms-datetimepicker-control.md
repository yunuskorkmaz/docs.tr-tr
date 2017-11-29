---
title: "Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme"
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
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4df12d196c02b1d868d395a10ca17abafaa0fb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Nasıl yapılır: Windows Forms DateTimePicker Denetimi ile Tarihleri Ayarlama ve Döndürme
Şu anda seçili tarih veya saat Windows Forms'ta <xref:System.Windows.Forms.DateTimePicker> denetim belirlenir <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği. Ayarlayabileceğiniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> denetimi görüntülenmeden önce özelliği (örneğin, tasarım zamanında veya formun <xref:System.Windows.Forms.Form.Load> olay) hangi tarih başlangıçta denetiminde seçilir belirlemek için. Varsayılan olarak, Denetim 's <xref:System.Windows.Forms.DateTimePicker.Value%2A> geçerli tarih olarak ayarlanır. Denetimin değiştirirseniz <xref:System.Windows.Forms.DateTimePicker.Value%2A> kodda denetimi yeni ayar yansıtmak için form üzerinde otomatik olarak güncelleştirilir.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Özelliği döndürür bir <xref:System.DateTime> yapısı değeri olarak. Çeşitli özellikleri vardır <xref:System.DateTime> görüntülenen tarih hakkındaki belirli bilgileri döndürmek yapısı. Bu özellikler, yalnızca bir değer döndürmek için kullanılabilir; bunları bir değer ayarlamak için kullanmayın.  
  
-   Tarih değerleri için <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, ve <xref:System.DateTime.Year%2A> özellikleri, seçilen tarihten bu zaman birimleri için tamsayı değerleri döndürür. <xref:System.DateTime.DayOfWeek%2A> Özelliği seçili haftanın gününü gösteren bir değeri döndürür (olası değerler olarak listelenen <xref:System.DayOfWeek> numaralandırması).  
  
-   Saat değerleri için <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, ve <xref:System.DateTime.Millisecond%2A> özellikleri için bu zaman birimlerini tamsayı değerleri döndürür. Sürelerini görüntülemek için denetimi yapılandırmak için bkz: [nasıl yapılır: DateTimePicker denetimiyle zamanı görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Denetimin tarih ve saat değeri ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.DateTimePicker.Value%2A> bir tarih veya saat değeri özelliğine.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Tarih ve saat değeri döndürmek için  
  
-   Çağrı <xref:System.Windows.Forms.DateTimePicker.Text%2A> denetiminde biçimli olarak tüm değerini döndürür veya uygun yöntemini çağırmak için özellik <xref:System.Windows.Forms.DateTimePicker.Value%2A> özelliği değerinin bir bölümünü döndürür. Kullanım <xref:System.Windows.Forms.DateTimePicker.ToString%2A> bilgileri kullanıcıya görüntülenen bir dizeye dönüştürmek için.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DateTimePicker denetimi](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DateTimePicker denetimi ile özel biçimde tarih görüntüleme](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
