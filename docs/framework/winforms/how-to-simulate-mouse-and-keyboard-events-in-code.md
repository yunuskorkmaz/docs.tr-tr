---
title: 'Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1a7a0fa6295cd8332313a983ca78345bfbac393e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046390"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="3093e-102">Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma</span><span class="sxs-lookup"><span data-stu-id="3093e-102">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="3093e-103">Windows Forms, fare ve klavye girişini programlı bir şekilde taklit etmek için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3093e-103">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="3093e-104">Bu konu, bu seçeneklere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3093e-104">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="3093e-105">Fare girişinin benzetimini yapma</span><span class="sxs-lookup"><span data-stu-id="3093e-105">Simulating Mouse Input</span></span>

<span data-ttu-id="3093e-106">Fare olaylarının benzetimini yapmanın en iyi yolu, benzetimini yapmak istediğiniz `On`fare olayını oluşturan *EventName* metodunu çağırmakdır.</span><span class="sxs-lookup"><span data-stu-id="3093e-106">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="3093e-107">Bu seçenek genellikle yalnızca özel denetimler ve formlarda yapılabilir, çünkü olayları oluşturan Yöntemler korunur ve denetim ya da form dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="3093e-107">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="3093e-108">Örneğin, aşağıdaki adımlarda kodda sağ fare düğmesine tıklanın simülasyonu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3093e-108">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="3093e-109">Programlama yoluyla sağ fare düğmesine tıklama</span><span class="sxs-lookup"><span data-stu-id="3093e-109">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="3093e-110">Bir <xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.MouseEventArgs.Button%2A> özelliği değereayarlanmışolanbirözellikoluşturun.<xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3093e-110">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="3093e-111">Bağımsız değişken olarak bu <xref:System.Windows.Forms.MouseEventArgs> yöntemiçağırın.<xref:System.Windows.Forms.Control.OnMouseClick%2A></span><span class="sxs-lookup"><span data-stu-id="3093e-111">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="3093e-112">Özel denetimler hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](./controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3093e-112">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="3093e-113">Fare girişinin benzetimini yapmak için başka yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="3093e-113">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="3093e-114">Örneğin, normalde fare girişi ( <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.CheckBox> denetimin özelliği gibi) aracılığıyla ayarlanmış olan bir durumu temsil eden bir denetim özelliğini program aracılığıyla ayarlayabilir veya size bağlı olan temsilciyi doğrudan çağırabilirsiniz benzetimi yapmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="3093e-114">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="3093e-115">Klavye girişi benzetimi yapma</span><span class="sxs-lookup"><span data-stu-id="3093e-115">Simulating Keyboard Input</span></span>

<span data-ttu-id="3093e-116">Fare girişi için yukarıda açıklanan stratejileri kullanarak klavye girişini benzeyseniz de Windows Forms, etkin uygulamaya tuş vuruşları göndermek <xref:System.Windows.Forms.SendKeys> için de sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3093e-116">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="3093e-117">Uygulamanız çeşitli klavyelerde uluslararası kullanım için tasarlanıyorsa, kullanımı <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> öngörülemeyen sonuçlara neden olabilir ve kaçınılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3093e-117">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="3093e-118"><xref:System.Windows.Forms.SendKeys> Sınıfı, Windows Vista 'da çalışan uygulamalarda kullanımını etkinleştirmek için .NET Framework 3,0 için güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3093e-118">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="3093e-119">Windows Vista 'nın (Kullanıcı hesabı denetimi veya UAC olarak bilinir) gelişmiş güvenliği, önceki uygulamanın beklendiği gibi çalışmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="3093e-119">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="3093e-120"><xref:System.Windows.Forms.SendKeys> Sınıf, bazı geliştiricilerin geçici bir çözüm sunmasıyla ilgili zamanlama sorunlarıyla açıktır.</span><span class="sxs-lookup"><span data-stu-id="3093e-120">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="3093e-121">Güncelleştirilmiş uygulama zamanlama sorunları için hala açıktır, ancak biraz daha hızlıdır ve geçici çözümler üzerinde değişiklik yapılmasını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="3093e-121">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="3093e-122"><xref:System.Windows.Forms.SendKeys> Sınıf önce önceki uygulamayı kullanmayı dener ve başarısız olursa yeni uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3093e-122">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="3093e-123">Sonuç olarak, <xref:System.Windows.Forms.SendKeys> sınıfı farklı işletim sistemlerinde farklı davranabilirler.</span><span class="sxs-lookup"><span data-stu-id="3093e-123">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="3093e-124">Ayrıca, <xref:System.Windows.Forms.SendKeys> sınıf yeni uygulamayı kullandığında <xref:System.Windows.Forms.SendKeys.SendWait%2A> , başka bir işleme gönderildiğinde, bu yöntem iletilerin işlenmesini beklemez.</span><span class="sxs-lookup"><span data-stu-id="3093e-124">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="3093e-125">Uygulamanız işletim sisteminden bağımsız olarak tutarlı davranış kullanıyorsa, App. config dosyanıza aşağıdaki uygulama ayarını ekleyerek <xref:System.Windows.Forms.SendKeys> sınıfı yeni uygulamayı kullanmaya zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3093e-125">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="3093e-126"><xref:System.Windows.Forms.SendKeys> Sınıfın önceki uygulamayı kullanmasını zorlamak için, bunun yerine değeri `"JournalHook"` kullanın.</span><span class="sxs-lookup"><span data-stu-id="3093e-126">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="3093e-127">Aynı uygulamaya bir tuş vuruşu göndermek için</span><span class="sxs-lookup"><span data-stu-id="3093e-127">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="3093e-128"><xref:System.Windows.Forms.SendKeys.Send%2A> <xref:System.Windows.Forms.SendKeys.SendWait%2A> Sınıfının veya<xref:System.Windows.Forms.SendKeys> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3093e-128">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="3093e-129">Belirtilen tuş vuruşları, uygulamanın etkin denetimi tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="3093e-129">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="3093e-130">Aşağıdaki kod örneği, Kullanıcı <xref:System.Windows.Forms.SendKeys.Send%2A> formun yüzeyine çift tıkladığında ENTER tuşuna basmanın benzetimini yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3093e-130">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="3093e-131">Bu örnek, bir <xref:System.Windows.Forms.Form> sekme dizini 0 <xref:System.Windows.Forms.Button> olan tek bir denetimin olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3093e-131">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="3093e-132">Farklı bir uygulamaya tuş vuruşu göndermek için</span><span class="sxs-lookup"><span data-stu-id="3093e-132">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="3093e-133">Tuş vuruşlarını alacak uygulama penceresini etkinleştirin ve sonra <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3093e-133">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="3093e-134">Başka bir uygulamayı etkinleştirmek için yönetilen bir yöntem olmadığından, başka uygulamalara odaklanmak için yerel Windows yöntemlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3093e-134">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="3093e-135">Aşağıdaki kod örneği, hesaplayıcı uygulama penceresini etkinleştirmek için `FindWindow` ve `SetForegroundWindow` yöntemlerini çağırmak üzere platform Invoke kullanır ve ardından hesaplayıcı uygulamasına <xref:System.Windows.Forms.SendKeys.SendWait%2A> bir dizi hesaplama vermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="3093e-135">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3093e-136">Hesap makinesi uygulamasını bulan `FindWindow` çağrının doğru parametreleri, Windows sürümünüze bağlı olarak değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="3093e-136">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="3093e-137">Aşağıdaki kod, üzerinde [!INCLUDE[win7](../../../includes/win7-md.md)]Hesaplayıcı uygulamasını bulur.</span><span class="sxs-lookup"><span data-stu-id="3093e-137">The following code finds the Calculator application on [!INCLUDE[win7](../../../includes/win7-md.md)].</span></span> <span data-ttu-id="3093e-138">Üzerinde [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], ilk parametreyi "SciCalc" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3093e-138">On [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], change the first parameter to "SciCalc".</span></span> <span data-ttu-id="3093e-139">Doğru parametreleri öğrenmek için Visual Studio ile birlikte bulunan Spy + + aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3093e-139">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="3093e-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="3093e-140">Example</span></span>

<span data-ttu-id="3093e-141">Aşağıdaki kod örneği, önceki kod örnekleri için tüm uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="3093e-141">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="3093e-142">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3093e-142">Compiling the Code</span></span>

<span data-ttu-id="3093e-143">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3093e-143">This example requires:</span></span>

- <span data-ttu-id="3093e-144">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="3093e-144">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3093e-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3093e-145">See also</span></span>

- [<span data-ttu-id="3093e-146">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="3093e-146">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
