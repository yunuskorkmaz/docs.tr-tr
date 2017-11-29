---
title: "Nasıl yapılır: Windows Forms MonthCalendar denetimi &#39; Değiştir s görünümü"
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
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38cddb4222077c21d72828371a8fe025184c4f75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Nasıl yapılır: Windows Forms MonthCalendar denetimi &#39; Değiştir s görünümü
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetim birçok yolla Takvim görünümünü özelleştirmenizi sağlar. Örneğin, renk düzenini ayarlama ve hafta numaralarını ve geçerli tarih görüntüleme veya gizleme seçin.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Ay takvim renk düzenini değiştirmek için  
  
-   Özellikleri ayarlamak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Özelliği için haftanın günlerini de yazı tipi rengini belirler. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Özelliği koyun ve görüntülenen ay ya da ay takip tarihleri rengini belirler.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  Temanın bağlı olarak Windows Vista ile başlayarak, bazı özelliklerin ayarlanmasını Takvim görünümünü değişmeyebilir. Örneğin, Windows Aero teması kullanmak üzere ayarlanmışsa ayarlama <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özellikleri etkisi yoktur. Takvim güncelleştirilmiş bir sürümünü çalışma zamanında geçerli işletim sistemi temayı türetilmiş bir görünümü ile işlenen olmasıdır. Bu özellikleri kullanın ve Takvim önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stiller devre dışı bırakabilirsiniz. Görsel stiller devre dışı bırakma görünümü ve davranışı, uygulamanızdaki diğer denetimlerin etkileyebilir. Visual Basic'te görsel stiller devre dışı bırakmak için Proje Tasarımcısı'nı açın ve kutusunun işaretini kaldırın **etkinleştirmek XP görsel stilleri** onay kutusu. C# görsel stiller devre dışı bırakmak için Program.cs açın ve çıkışı açıklama `Application.EnableVisualStyles();`. Görsel stiller hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows XP görsel stilleri etkinleştir](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Geçerli tarih denetimi altında görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğine `true`. Aşağıdaki örnek, görüntüleme ve form tıklatıldığında olduğunda bugünün tarihini atlama arasında geçiş yapar.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Hafta numaralarını görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğine `true`. Bu özellik, kod veya özellikleri penceresinde ayarlayabilirsiniz.  
  
     Haftanın ilk günü soluna ayrı bir sütunda hafta numaraları görünür.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MonthCalendar denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminde tarih aralığı seçin](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Nasıl yapılır: belirli günleri kalın olarak görüntüleme Windows Forms MonthCalendar denetimi](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar denetiminde birden fazla ay görüntüleme](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
