---
title: "Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma"
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
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 716de57574beef55d066a3bb121a6fc19a4959d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma
Bazen belirli zaman aralıklarında bir döngü sona erdi veya ayarlanmış bir zaman aralığından geçtiğinde çalıştıran kadar çalıştıran bir yordam oluşturmak isteyebilirsiniz. <xref:System.Windows.Forms.Timer> Bileşen bu tür bir yordam olanaklı kılar.  
  
 Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Bazı sınırlamalar vardır kullanırken <xref:System.Windows.Forms.Timer> bileşeni. Daha fazla bilgi için bkz: [Windows Forms süreölçer bileşeninin aralık özelliği sınırlamaları](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Süreölçer bileşeni ile belirlenen aralıklarda bir yordamı çalıştırmak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.Timer> formunuza. Bu program aracılığıyla yapmak nasıl bir çizimi için aşağıdaki örnek bölümüne bakın. [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]bileşenleri bir forma ekleme desteği de vardır. Ayrıca bkz. [nasıl yapılır: ekleme denetimleri olmadan bir kullanıcı arabirimine Windows Forms](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> Zamanlayıcı için özelliği (milisaniye cinsinden). Bu özellik, yordamı tekrar çalıştırmadan önce ne kadar süre geçer belirler.  
  
    > [!NOTE]
    >  Daha sık süreölçer olayı oluşur, daha fazla işlemci zamanı olaya yanıt olarak kullanılır. Bu genel performansını yavaşlatabilir. Gereksinim duyduğunuz daha küçük bir aralık ayarlı değil.  
  
3.  Uygun kodu yazmak <xref:System.Windows.Forms.Timer.Tick> olay işleyicisi. Bu durumda yazma kodu, belirtilen aralıkta çalıştıracak <xref:System.Windows.Forms.Timer.Interval%2A> özelliği.  
  
4.  Ayarlama <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğine `true` süreölçeri başlatmak için. <xref:System.Windows.Forms.Timer.Tick> Olay başlayacak gerçekleşmesi belirlenen aralıkta yordamınız çalışıyor.  
  
5.  Uygun sırada ayarlamak <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğine `false` yeniden çalışmasını yordamı durdurmak için. Aralığı ayarını `0` durdurmak Zamanlayıcı neden olmaz.  
  
## <a name="example"></a>Örnek  
 Bu ilk örnek kod bir saniyelik artışlarla günün saatini izler. Kullandığı bir <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>ve bir <xref:System.Windows.Forms.Timer> bir form üzerinde bileşen. <xref:System.Windows.Forms.Timer.Interval%2A> Özelliği 1000 (bir saniye eşit) olarak ayarlanmış. İçinde <xref:System.Windows.Forms.Timer.Tick> olay, etiketin resim yazısı geçerli saate ayarlanır. Düğme tıklatıldığında <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği ayarlanmış `false`, etiketin resim yazısı güncelleştirme gelen zamanlayıcı durduruluyor. Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1`, <xref:System.Windows.Forms.Timer> adlı Denetim `Timer1`ve bir <xref:System.Windows.Forms.Label> adlı Denetim `Label1`.  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>Örnek  
 Döngü tamamlanana kadar bu ikinci kod örneği bir yordam her 600 milisaniye çalışır. Aşağıdaki kod örneğinde bir formla sahip olmasını gerektiren bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1`, <xref:System.Windows.Forms.Timer> adlı Denetim `Timer1`ve bir <xref:System.Windows.Forms.Label> adlı Denetim `Label1`.  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Timer>  
 [Süreölçer Bileşeni](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Süreölçer Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
