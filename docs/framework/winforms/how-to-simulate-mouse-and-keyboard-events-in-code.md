---
title: "Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma"
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
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b764533b845ddf1585c9b3de9eb6283ec5ec6ea
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="1586b-102">Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma</span><span class="sxs-lookup"><span data-stu-id="1586b-102">How to: Simulate Mouse and Keyboard Events in Code</span></span>
<span data-ttu-id="1586b-103">Windows Forms program aracılığıyla fare ve klavye girdisi benzetimi için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1586b-103">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="1586b-104">Bu konu, bu seçenekleri genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1586b-104">This topic provides an overview of these options.</span></span>  
  
## <a name="simulating-mouse-input"></a><span data-ttu-id="1586b-105">Fare girişi benzetimini yapma</span><span class="sxs-lookup"><span data-stu-id="1586b-105">Simulating Mouse Input</span></span>  
 <span data-ttu-id="1586b-106">Fare olayları benzetimini yapmak için en iyi yolu çağırmaktır `On` *EventName* benzetimini yapmak istediğiniz fare olayını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1586b-106">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="1586b-107">Olaylarını yöntemleri korunur ve denetim veya formun dışında erişilemez olduğundan bu seçenek yalnızca özel denetimler ve formları içinde genellikle mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1586b-107">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="1586b-108">Örneğin, aşağıdaki adımları kodda sağ fare düğmesini tıklatarak benzetimini yapma gösterir.</span><span class="sxs-lookup"><span data-stu-id="1586b-108">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="1586b-109">Program aracılığıyla farenin sağ düğmesiyle tıklatın</span><span class="sxs-lookup"><span data-stu-id="1586b-109">To programmatically click the right mouse button</span></span>  
  
1.  <span data-ttu-id="1586b-110">Oluşturma bir <xref:System.Windows.Forms.MouseEventArgs> , <xref:System.Windows.Forms.MouseEventArgs.Button%2A> özelliği ayarlanmış <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="1586b-110">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>  
  
2.  <span data-ttu-id="1586b-111">Çağrı <xref:System.Windows.Forms.Control.OnMouseClick%2A> bu yöntemle <xref:System.Windows.Forms.MouseEventArgs> bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="1586b-111">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>  
  
 <span data-ttu-id="1586b-112">Özel denetimler hakkında daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="1586b-112">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span>  
  
 <span data-ttu-id="1586b-113">Fare girişi benzetimini yapmak için başka yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="1586b-113">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="1586b-114">Örneğin, program aracılığıyla genellikle fare girdisi ayarlanır durumunu temsil eden bir denetim özelliğini ayarlayabilirsiniz (gibi <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği <xref:System.Windows.Forms.CheckBox> denetimi), ya da olaya bağlı temsilci doğrudan çağırabilir miyim, benzetimini yapmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="1586b-114">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>  
  
## <a name="simulating-keyboard-input"></a><span data-ttu-id="1586b-115">Klavye girişi benzetimini yapma</span><span class="sxs-lookup"><span data-stu-id="1586b-115">Simulating Keyboard Input</span></span>  
 <span data-ttu-id="1586b-116">Yukarıda Windows Forms de sağlar fare girdisi için açıklanan stratejileri kullanarak klavye girişi benzetimini yapabilirsiniz ancak <xref:System.Windows.Forms.SendKeys> etkin uygulamaya tuş vuruşları göndermek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1586b-116">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1586b-117">Uygulamanızı klavyeler, kullanımını çeşitli uluslararası kullanmaya yönelik varsa <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> beklenmeyen sonuçlar ve kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1586b-117">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1586b-118"><xref:System.Windows.Forms.SendKeys> Sınıfı, Windows Vista üzerinde çalışan uygulamaları kullanımını etkinleştirmek .NET Framework 3.0 için güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1586b-118">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="1586b-119">Windows Vista'nın (kullanıcı hesabı denetimi veya UAC da bilinir) Artırılmış güvenlik, beklendiği gibi çalışmasını önceki uygulaması engeller.</span><span class="sxs-lookup"><span data-stu-id="1586b-119">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>  
>   
>  <span data-ttu-id="1586b-120"><xref:System.Windows.Forms.SendKeys> Sınıfı, bazı geliştiriciler çözmek zorunda zamanlama sorunları için açıktır.</span><span class="sxs-lookup"><span data-stu-id="1586b-120">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="1586b-121">Güncelleştirilmiş uygulama zamanlama sorunları için hala açıktır, ancak biraz daha hızlıdır ve geçici çözümler değişiklikler gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="1586b-121">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="1586b-122"><xref:System.Windows.Forms.SendKeys> Sınıfı önceki uygulaması kullanmayı dener ve başarısız olursa, yeni uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="1586b-122">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="1586b-123">Sonuç olarak, <xref:System.Windows.Forms.SendKeys> sınıfı davranır farklı farklı işletim sistemleri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1586b-123">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="1586b-124">Ayrıca, <xref:System.Windows.Forms.SendKeys> sınıfını kullanan yeni uygulama <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi için başka bir işleme gönderildiğinde işlenecek iletilerinin değil bekleyecek.</span><span class="sxs-lookup"><span data-stu-id="1586b-124">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>  
>   
>  <span data-ttu-id="1586b-125">Uygulamanız işletim sistemi bağımsız olarak tutarlı davranışına dayalıysa, zorlayabilirsiniz <xref:System.Windows.Forms.SendKeys> sınıfı, app.config dosyasına aşağıdaki uygulama ayarı ekleyerek yeni uygulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="1586b-125">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  <span data-ttu-id="1586b-126">Zorlamak için <xref:System.Windows.Forms.SendKeys> önceki uygulaması, değer kullanmanız için sınıf `"JournalHook"` yerine.</span><span class="sxs-lookup"><span data-stu-id="1586b-126">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="1586b-127">Aynı uygulamaya bir tuş vuruşu göndermek için</span><span class="sxs-lookup"><span data-stu-id="1586b-127">To send a keystroke to the same application</span></span>  
  
1.  <span data-ttu-id="1586b-128">Çağrı <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi <xref:System.Windows.Forms.SendKeys> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1586b-128">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="1586b-129">Belirtilen tuş vuruşları uygulama etkin denetim alınır.</span><span class="sxs-lookup"><span data-stu-id="1586b-129">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="1586b-130">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.SendKeys.Send%2A> kullanıcı formu yüzeyinin tıklattığında ENTER tuşuna basarak benzetimini yapmak için.</span><span class="sxs-lookup"><span data-stu-id="1586b-130">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="1586b-131">Bu örnek varsayar bir <xref:System.Windows.Forms.Form> tek bir <xref:System.Windows.Forms.Button> bir sekme dizini 0 olan denetim.</span><span class="sxs-lookup"><span data-stu-id="1586b-131">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="1586b-132">Farklı bir uygulamaya bir tuş vuruşu göndermek için</span><span class="sxs-lookup"><span data-stu-id="1586b-132">To send a keystroke to a different application</span></span>  
  
1.  <span data-ttu-id="1586b-133">Tuş vuruşları almak, ardından çağıran uygulama penceresi etkinleştirme <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1586b-133">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="1586b-134">Başka bir uygulamayı etkinleştirmek için yönetilen bir yöntem olduğundan, diğer uygulamaları odak zorlamak için yerel Windows yöntemlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1586b-134">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="1586b-135">Aşağıdaki kod örneği kullanan platform çağırma çağırmak için `FindWindow` ve `SetForegroundWindow` hesaplayıcı uygulama penceresi, ardından çağrıları etkinleştirmek için yöntemleri <xref:System.Windows.Forms.SendKeys.SendWait%2A> hesaplamaları bir dizi hesaplayıcı uygulamaya vermek için.</span><span class="sxs-lookup"><span data-stu-id="1586b-135">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1586b-136">Doğru parametreleri `FindWindow` hesaplayıcı uygulama bulur çağrısı Windows sürümüne göre değişir.</span><span class="sxs-lookup"><span data-stu-id="1586b-136">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="1586b-137">Aşağıdaki kod üzerinde hesaplayıcı uygulama bulur [!INCLUDE[win7](../../../includes/win7-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1586b-137">The following code finds the Calculator application on [!INCLUDE[win7](../../../includes/win7-md.md)].</span></span> <span data-ttu-id="1586b-138">Üzerinde [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], ilk parametre "SciCalc" değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1586b-138">On [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], change the first parameter to "SciCalc".</span></span> <span data-ttu-id="1586b-139">Visual Studio ile dahil Spy ++ araç, doğru parametreleri belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1586b-139">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1586b-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="1586b-140">Example</span></span>  
 <span data-ttu-id="1586b-141">Aşağıdaki kod örneği, yukarıdaki kod örnekleri için tam uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1586b-141">The following code example is the complete application for the previous code examples.</span></span>  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1586b-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1586b-142">Compiling the Code</span></span>  
 <span data-ttu-id="1586b-143">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1586b-143">This example requires:</span></span>  
  
-   <span data-ttu-id="1586b-144">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1586b-144">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1586b-145">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1586b-145">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1586b-146">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="1586b-146">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="1586b-147">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1586b-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1586b-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1586b-148">See Also</span></span>  
 [<span data-ttu-id="1586b-149">Windows Forms uygulamasında kullanıcı girdisi</span><span class="sxs-lookup"><span data-stu-id="1586b-149">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
