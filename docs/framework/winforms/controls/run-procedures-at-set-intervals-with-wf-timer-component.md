---
title: 'Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma'
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
ms.openlocfilehash: ac2f89619c3e87ebfe5e568bbf27274834b0866d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325026"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="c824c-102">Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c824c-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="c824c-103">Bazen bir döngü sona veya bir kümesi zaman aralığı süresi sona erdiğinde çalıştırılan kadar belirli aralıklarla çalışan bir yordam oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c824c-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="c824c-104"><xref:System.Windows.Forms.Timer> Bileşeni gibi bir yordam mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="c824c-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="c824c-105">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c824c-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="c824c-106">Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c824c-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c824c-107">Kullanırken bazı sınırlamalar uygulanır <xref:System.Windows.Forms.Timer> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c824c-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="c824c-108">Daha fazla bilgi için [Windows Forms süreölçer bileşeninin aralık özelliğiyle ilgili sınırlamalar](limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="c824c-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](limitations-of-the-timer-component-interval-property.md).</span></span>  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="c824c-109">Süreölçer bileşeni ile belirlenen aralıklarda bir yordamı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c824c-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1. <span data-ttu-id="c824c-110">Ekleme bir <xref:System.Windows.Forms.Timer> formunuza.</span><span class="sxs-lookup"><span data-stu-id="c824c-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="c824c-111">Bu program aracılığıyla yapmak nasıl bir gösterimi için aşağıdaki örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c824c-111">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="c824c-112">Visual Studio, bileşenlerin bir forma ekleme desteği de sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c824c-112">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="c824c-113">Ayrıca bkz: [nasıl yapılır: Windows Forms'a kullanıcı arabirimi olmadan denetimler ekleme](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c824c-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="c824c-114">Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> Zamanlayıcı özelliği (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="c824c-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="c824c-115">Bu özellik, yordam yeniden çalıştırmadan önce ne kadar süre geçer belirler.</span><span class="sxs-lookup"><span data-stu-id="c824c-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c824c-116">Bir zamanlayıcı olaylarının daha sık, daha fazla işlemci zamanı olaya yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c824c-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="c824c-117">Bu genel performansını yavaşlatabilir.</span><span class="sxs-lookup"><span data-stu-id="c824c-117">This can slow down overall performance.</span></span> <span data-ttu-id="c824c-118">İhtiyacınız olandan daha küçük bir aralık ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="c824c-118">Do not set a smaller interval than you need.</span></span>  
  
3. <span data-ttu-id="c824c-119">Uygun kod yazmaya <xref:System.Windows.Forms.Timer.Tick> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c824c-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="c824c-120">Bu olay, yazdığınız kod içinde belirtilen aralıkta çalışacak <xref:System.Windows.Forms.Timer.Interval%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c824c-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4. <span data-ttu-id="c824c-121">Ayarlama <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `true` zamanlayıcıyı başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="c824c-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="c824c-122"><xref:System.Windows.Forms.Timer.Tick> Olay başlayacak gerçekleşmesi, belirlenen aralıkta yordamınız çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="c824c-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5. <span data-ttu-id="c824c-123">Uygun ayarlarken <xref:System.Windows.Forms.Timer.Enabled%2A> özelliğini `false` yordamı yeniden çalışmasını durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="c824c-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="c824c-124">Aralığı ayarını `0` durdurmak Zamanlayıcı neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="c824c-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c824c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="c824c-125">Example</span></span>  
 <span data-ttu-id="c824c-126">Bu ilk kod örneği, bir saniyelik artışlarla günün saatini izler.</span><span class="sxs-lookup"><span data-stu-id="c824c-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="c824c-127">Bunu kullanan bir <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>ve <xref:System.Windows.Forms.Timer> formdaki bileşen.</span><span class="sxs-lookup"><span data-stu-id="c824c-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="c824c-128"><xref:System.Windows.Forms.Timer.Interval%2A> Değerini 1000'e (bir saniyeye eşit) özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c824c-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="c824c-129">İçinde <xref:System.Windows.Forms.Timer.Tick> olay, etiketin açıklamalı alt yazı geçerli saate ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c824c-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="c824c-130">Düğme tıklandığında <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği `false`, etiketin açıklamalı alt yazı güncelleştirme gelen zamanlayıcı durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="c824c-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="c824c-131">Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1`, <xref:System.Windows.Forms.Timer> adlı Denetim `Timer1`ve <xref:System.Windows.Forms.Label> adlı Denetim `Label1`.</span><span class="sxs-lookup"><span data-stu-id="c824c-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c824c-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="c824c-132">Example</span></span>  
 <span data-ttu-id="c824c-133">Bir döngü tamamlanana kadar bu ikinci kod örneğinde bir yordam her 600 milisaniye çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c824c-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="c824c-134">Aşağıdaki kod örneği, bir form olmasını gerektirir bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1`, <xref:System.Windows.Forms.Timer> adlı Denetim `Timer1`ve <xref:System.Windows.Forms.Label> adlı Denetim `Label1`.</span><span class="sxs-lookup"><span data-stu-id="c824c-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c824c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c824c-135">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="c824c-136">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="c824c-136">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="c824c-137">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c824c-137">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
