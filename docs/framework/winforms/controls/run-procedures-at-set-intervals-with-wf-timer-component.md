---
title: Zamanlayıcı bileşeniyle belirlenen aralıklarda yordamları çalıştırma
ms.date: 03/30/2017
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
ms.openlocfilehash: dcc88beee947e2a83b426dcd2f3fd9d70c20fb67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743118"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma
Bazen bir döngü bitene veya bir küme zaman aralığı geçtiğinde çalıştıktan sonra belirli zaman aralıklarında çalışan bir yordam oluşturmak isteyebilirsiniz. <xref:System.Windows.Forms.Timer> bileşeni, böyle bir yordamı mümkün hale getirir.  
  
 Bu bileşen bir Windows Forms ortamı için tasarlanmıştır. Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> <xref:System.Windows.Forms.Timer> bileşeni kullanılırken bazı sınırlamalar vardır. Daha fazla bilgi için [Windows Forms Süreölçer Bileşeninin Aralık özelliğinin sınırlamaları](limitations-of-the-timer-component-interval-property.md)bölümüne bakın.  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Zamanlayıcı bileşeniyle ayarlama aralıklarında bir yordamı çalıştırmak için  
  
1. Formunuza bir <xref:System.Windows.Forms.Timer> ekleyin. Bunun programlı olarak nasıl yapılacağını gösteren bir çizim için aşağıdaki örnek bölümüne bakın. Visual Studio, forma bileşen ekleme desteği de içerir. Ayrıca bkz. [nasıl yapılır: Kullanıcı arabirimi olmadan denetim ekleme Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. Zamanlayıcı için <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini (milisaniye cinsinden) ayarlayın. Bu özellik, yordam yeniden çalıştırılmadan önce ne kadar zaman geçirileceğini belirler.  
  
    > [!NOTE]
    > Daha sık bir zamanlayıcı olayı gerçekleştiğinde, olaya yanıt vermek için daha fazla işlemci zamanı kullanılır. Bu, genel performansı yavaşlatabilir. İhtiyacınız olandan daha küçük bir Aralık ayarlamayın.  
  
3. <xref:System.Windows.Forms.Timer.Tick> olay işleyicisine uygun kodu yazın. Bu olaya yazdığınız kod <xref:System.Windows.Forms.Timer.Interval%2A> özelliğinde belirtilen aralıkta çalışacaktır.  
  
4. Zamanlayıcıyı başlatmak için <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true` olarak ayarlayın. <xref:System.Windows.Forms.Timer.Tick> olay, bir süre sonra, yordamı küme aralığı üzerinde çalıştırmaya başlar.  
  
5. Uygun zamanda, yordamı yeniden çalıştırmayı durdurmak için <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `false` olarak ayarlayın. Aralığı `0` olarak ayarlamak, zamanlayıcının durmasına neden olmaz.  
  
## <a name="example"></a>Örnek  
 Bu ilk kod örneği, tek saniyelik artışlarla günün saatini izler. Bir form üzerinde <xref:System.Windows.Forms.Button>, bir <xref:System.Windows.Forms.Label>ve <xref:System.Windows.Forms.Timer> bileşeni kullanır. <xref:System.Windows.Forms.Timer.Interval%2A> özelliği 1000 (bir saniyeye eşit) olarak ayarlanır. <xref:System.Windows.Forms.Timer.Tick> olayında etiketin başlık yazısı geçerli saate ayarlanır. Düğmeye tıklandığında, <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği `false`olarak ayarlanır, bu da zamanlayıcıyı etiketin açıklamalı alt yazısının güncelleştirilmesini durduruyor. Aşağıdaki kod örneği, `Button1`adlı bir <xref:System.Windows.Forms.Button> denetimi, `Timer1`adlı bir <xref:System.Windows.Forms.Timer> denetimi ve <xref:System.Windows.Forms.Label> adlı `Label1`denetimini içeren bir formunuz olmasını gerektirir.  
  
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
 Bu ikinci kod örneği, bir döngü bitene kadar her 600 milisaniyede bir yordam çalıştırır. Aşağıdaki kod örneği, `Button1`adlı bir <xref:System.Windows.Forms.Button> denetimi, `Timer1`adlı bir <xref:System.Windows.Forms.Timer> denetimi ve <xref:System.Windows.Forms.Label> adlı `Label1`denetimini içeren bir formunuz olmasını gerektirir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Süreölçer Bileşenine Genel Bakış](timer-component-overview-windows-forms.md)
