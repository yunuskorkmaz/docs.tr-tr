---
title: Zamanlayıcı bileşeniyle belirlenen aralıklarda yordamları çalıştırma
description: Belirli aralıklarla veya bir ayarlama zaman aralığı geçtiğinde yordamları çalıştırmak için Windows form Zamanlayıcı bileşenini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 6847819fcec98d01d38b8e44604a259f06be7c02
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325765"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="bf5f4-103">Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bf5f4-103">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="bf5f4-104">Bazen bir döngü bitene veya bir küme zaman aralığı geçtiğinde çalıştıktan sonra belirli zaman aralıklarında çalışan bir yordam oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-104">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="bf5f4-105"><xref:System.Windows.Forms.Timer>Bileşen böyle bir yordamı mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-105">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="bf5f4-106">Bu bileşen bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-106">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="bf5f4-107">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bf5f4-107">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf5f4-108">Bileşeni kullanırken bazı sınırlamalar vardır <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="bf5f4-108">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="bf5f4-109">Daha fazla bilgi için [Windows Forms Süreölçer Bileşeninin Aralık özelliğinin sınırlamaları](limitations-of-the-timer-component-interval-property.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-109">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](limitations-of-the-timer-component-interval-property.md).</span></span>  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="bf5f4-110">Zamanlayıcı bileşeniyle ayarlama aralıklarında bir yordamı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bf5f4-110">To run a procedure at set intervals with the Timer component</span></span>  
  
1. <span data-ttu-id="bf5f4-111">Formunuza bir ekleyin <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="bf5f4-111">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="bf5f4-112">Bunun programlı olarak nasıl yapılacağını gösteren bir çizim için aşağıdaki örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-112">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="bf5f4-113">Visual Studio, forma bileşen ekleme desteği de içerir.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-113">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="bf5f4-114">Ayrıca bkz. [nasıl yapılır: Kullanıcı arabirimi olmadan denetim ekleme Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bf5f4-114">Also see [How to: Add Controls Without a User Interface to Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="bf5f4-115"><xref:System.Windows.Forms.Timer.Interval%2A>Süreölçer için özelliği (milisaniye olarak) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-115">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="bf5f4-116">Bu özellik, yordam yeniden çalıştırılmadan önce ne kadar zaman geçirileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-116">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf5f4-117">Daha sık bir zamanlayıcı olayı gerçekleştiğinde, olaya yanıt vermek için daha fazla işlemci zamanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-117">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="bf5f4-118">Bu, genel performansı yavaşlatabilir.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-118">This can slow down overall performance.</span></span> <span data-ttu-id="bf5f4-119">İhtiyacınız olandan daha küçük bir Aralık ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-119">Do not set a smaller interval than you need.</span></span>  
  
3. <span data-ttu-id="bf5f4-120">Olay işleyicisine uygun kodu yazın <xref:System.Windows.Forms.Timer.Tick> .</span><span class="sxs-lookup"><span data-stu-id="bf5f4-120">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="bf5f4-121">Bu olaya yazdığınız kod, özelliğinde belirtilen aralıkta çalışır <xref:System.Windows.Forms.Timer.Interval%2A> .</span><span class="sxs-lookup"><span data-stu-id="bf5f4-121">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4. <span data-ttu-id="bf5f4-122"><xref:System.Windows.Forms.Timer.Enabled%2A> `true` Zamanlayıcıyı başlatmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-122">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="bf5f4-123">Olay, bir <xref:System.Windows.Forms.Timer.Tick> süre sonra, prosedürü ayarlanan aralıkta çalıştırılarak gerçekleştirilecek şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-123">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5. <span data-ttu-id="bf5f4-124">Uygun zamanda, <xref:System.Windows.Forms.Timer.Enabled%2A> `false` yordamını yeniden çalıştırmayı durdurmak için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-124">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="bf5f4-125">Aralığı `0` Zamanlayıcı 'nın durdurulmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-125">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf5f4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf5f4-126">Example</span></span>  
 <span data-ttu-id="bf5f4-127">Bu ilk kod örneği, tek saniyelik artışlarla günün saatini izler.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-127">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="bf5f4-128"><xref:System.Windows.Forms.Button>Form üzerinde bir,, <xref:System.Windows.Forms.Label> ve bir <xref:System.Windows.Forms.Timer> bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-128">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="bf5f4-129"><xref:System.Windows.Forms.Timer.Interval%2A>Özelliği 1000 (bir saniyeye eşit) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-129">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="bf5f4-130"><xref:System.Windows.Forms.Timer.Tick>Olayda, etiketin başlık yazısı geçerli saate ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-130">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="bf5f4-131">Düğmeye tıklandığında, <xref:System.Windows.Forms.Timer.Enabled%2A> özelliği olarak ayarlanır, bu da `false` süreölçer 'in etiketin açıklamalı alt yazısının güncelleştirilmesini durdurulur.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-131">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="bf5f4-132">Aşağıdaki kod örneği, adlı bir denetim <xref:System.Windows.Forms.Button> `Button1` , adlı bir denetim <xref:System.Windows.Forms.Timer> `Timer1` ve <xref:System.Windows.Forms.Label> adlı `Label1` bir denetim içeren bir formunuz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-132">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bf5f4-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf5f4-133">Example</span></span>  
 <span data-ttu-id="bf5f4-134">Bu ikinci kod örneği, bir döngü bitene kadar her 600 milisaniyede bir yordam çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-134">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="bf5f4-135">Aşağıdaki kod örneği, adlı bir denetim <xref:System.Windows.Forms.Button> `Button1` , adlı bir denetim <xref:System.Windows.Forms.Timer> `Timer1` ve <xref:System.Windows.Forms.Label> adlı `Label1` bir denetim içeren bir formunuz olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-135">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf5f4-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-136">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="bf5f4-137">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="bf5f4-137">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="bf5f4-138">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bf5f4-138">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
