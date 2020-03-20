---
title: Zamanlayıcı Bileşeni ile Ayarlı Aralıklarda Yordamları Çalıştır
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
ms.openlocfilehash: 52d68a8136551384f67ff6232799600af09f8b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182053"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="ea780-102">Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ea780-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="ea780-103">Bazen bir döngü bitene veya belirli bir zaman aralığı dolduğunda çalışana kadar belirli zaman aralıklarında çalışan bir yordam oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea780-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="ea780-104">Bileşen <xref:System.Windows.Forms.Timer> böyle bir yordamı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="ea780-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="ea780-105">Bu bileşen, Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ea780-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="ea780-106">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa, [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ea780-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea780-107"><xref:System.Windows.Forms.Timer> Bileşeni kullanırken bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="ea780-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="ea780-108">Daha fazla bilgi için Bkz. [Windows Formlar Zamanlayıcı Bileşeninin Interval Özelliğinin Sınırlamaları.](limitations-of-the-timer-component-interval-property.md)</span><span class="sxs-lookup"><span data-stu-id="ea780-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](limitations-of-the-timer-component-interval-property.md).</span></span>  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="ea780-109">Zamanlayıcı bileşeni ile belirli aralıklarla bir yordam çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ea780-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1. <span data-ttu-id="ea780-110">Formunuza <xref:System.Windows.Forms.Timer> bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ea780-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="ea780-111">Bunu programlı olarak nasıl yapacağınız ile ilgili bir resim için aşağıdaki Örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ea780-111">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="ea780-112">Visual Studio da bir forma bileşenleri eklemek için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="ea780-112">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="ea780-113">Ayrıca [bkz.](how-to-add-controls-without-a-user-interface-to-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ea780-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="ea780-114">Zamanlayıcının özelliğini <xref:System.Windows.Forms.Timer.Interval%2A> (milisaniye cinsinden) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ea780-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="ea780-115">Bu özellik, yordam yeniden çalıştırılmadan önce ne kadar zaman geçeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ea780-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ea780-116">Zamanlayıcı olayı ne kadar sık gerçekleşirse, olaya yanıt vermede o kadar çok işlemci süresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ea780-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="ea780-117">Bu, genel performansı yavaşlatabilir.</span><span class="sxs-lookup"><span data-stu-id="ea780-117">This can slow down overall performance.</span></span> <span data-ttu-id="ea780-118">İhtiyacınız olandan daha küçük bir aralık ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="ea780-118">Do not set a smaller interval than you need.</span></span>  
  
3. <span data-ttu-id="ea780-119">Olay işleyicisi <xref:System.Windows.Forms.Timer.Tick> uygun kod yazın.</span><span class="sxs-lookup"><span data-stu-id="ea780-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="ea780-120">Bu olayda yazdığınız <xref:System.Windows.Forms.Timer.Interval%2A> kod, özellikte belirtilen aralıkta çalışır.</span><span class="sxs-lookup"><span data-stu-id="ea780-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4. <span data-ttu-id="ea780-121">Özelliği <xref:System.Windows.Forms.Timer.Enabled%2A> zamanlayıcıyı başlatmak için `true` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ea780-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="ea780-122">Yordamınızı <xref:System.Windows.Forms.Timer.Tick> ayarlanan aralıkta çalıştırarak olay oluşmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="ea780-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5. <span data-ttu-id="ea780-123">Uygun zamanda, yordamın <xref:System.Windows.Forms.Timer.Enabled%2A> yeniden `false` çalışmasını durdurmak için özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ea780-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="ea780-124">Aralığı ayarlamak `0` zamanlayıcının durmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="ea780-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea780-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea780-125">Example</span></span>  
 <span data-ttu-id="ea780-126">Bu ilk kod örneği, bir saniyelik artışlarla günün saatini izler.</span><span class="sxs-lookup"><span data-stu-id="ea780-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="ea780-127">Bir form <xref:System.Windows.Forms.Button>üzerinde <xref:System.Windows.Forms.Label>bir <xref:System.Windows.Forms.Timer> , a ve bileşen kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea780-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="ea780-128">Özellik <xref:System.Windows.Forms.Timer.Interval%2A> 1000 olarak ayarlanır (bir saniyeye eşittir).</span><span class="sxs-lookup"><span data-stu-id="ea780-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="ea780-129"><xref:System.Windows.Forms.Timer.Tick> Olayda, etiketin resim yazısı geçerli saate ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ea780-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="ea780-130">Düğme tıklatıldığında, <xref:System.Windows.Forms.Timer.Enabled%2A> özellik `false`zamanlayıcının etiketin alt yazısını güncelleştirmesini durduracak şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ea780-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="ea780-131"><xref:System.Windows.Forms.Button> Aşağıdaki kod örneği, adlı `Button1` <xref:System.Windows.Forms.Timer> `Timer1`bir denetim , bir denetim ve <xref:System.Windows.Forms.Label> adlı `Label1`bir denetim ile bir form gerektirir .</span><span class="sxs-lookup"><span data-stu-id="ea780-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ea780-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea780-132">Example</span></span>  
 <span data-ttu-id="ea780-133">Bu ikinci kod örneği, bir döngü bitene kadar her 600 milisaniyede bir yordam çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea780-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="ea780-134"><xref:System.Windows.Forms.Button> Aşağıdaki kod örneği, adlı `Button1` <xref:System.Windows.Forms.Timer> `Timer1`bir denetim , bir denetim ve <xref:System.Windows.Forms.Label> adlı `Label1`bir denetim ile bir form gerektirir .</span><span class="sxs-lookup"><span data-stu-id="ea780-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea780-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea780-135">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="ea780-136">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ea780-136">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="ea780-137">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ea780-137">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
