---
title: 'Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 45df54b3a590078eff6ddc1197db5b0124663cf5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971912"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="bf7f8-102">Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bf7f8-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>

<span data-ttu-id="bf7f8-103">Bu denetimi, <xref:System.Windows.Forms.WebBrowser> Windows Forms istemci uygulamalarınıza var olan dinamik HTML (DHTML) Web uygulaması kodu eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="bf7f8-104">Bu, DHTML tabanlı denetimler oluşturma konusunda önemli bir geliştirme süresi yatırdığınızda ve mevcut kodu yeniden yazmak zorunda kalmadan Windows Forms zengin Kullanıcı arabirimi özellikleri avantajlarından yararlanmak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>

<span data-ttu-id="bf7f8-105">Denetim, <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> ve<xref:System.Windows.Forms.WebBrowser.Document%2A> özellikleri aracılığıyla istemci uygulama kodunuz ile Web sayfanızın betik oluşturma kodu arasında iki yönlü iletişim uygulamanıza olanak sağlar. <xref:System.Windows.Forms.WebBrowser></span><span class="sxs-lookup"><span data-stu-id="bf7f8-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="bf7f8-106">Ayrıca, <xref:System.Windows.Forms.WebBrowser> denetimi, Web denetimlerinizin uygulama formunuzdaki diğer denetimlerle sorunsuz bir şekilde karışmasını sağlayacak şekilde, DHTML uygulamasını gizleyerek yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="bf7f8-107">Denetimleri sorunsuzca karıştırmak için, sayfanın arka plan rengi ve görsel stilinin formun geri kalanıyla eşleşmesi için görüntülenen sayfayı biçimlendirin ve standart tarayıcı özelliklerini devre dışı bırakmak için <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>ve <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="bf7f8-108">Windows Forms uygulamanıza DHTML eklemek için</span><span class="sxs-lookup"><span data-stu-id="bf7f8-108">To embed DHTML in your Windows Forms application</span></span>

1. <span data-ttu-id="bf7f8-109">Denetimin üzerinde bırakılan dosyaları <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> açmasını engellemek `false` için denetiminözelliğiniolarakayarlayın.<xref:System.Windows.Forms.WebBrowser> <xref:System.Windows.Forms.WebBrowser></span><span class="sxs-lookup"><span data-stu-id="bf7f8-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. <span data-ttu-id="bf7f8-110">Kullanıcı sağ tıkladığında <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> <xref:System.Windows.Forms.WebBrowser> denetimin kısayol menüsünü `false` görüntülemesini engellemek için denetimin özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. <span data-ttu-id="bf7f8-111">Denetimin kısayol tuşlarına yanıt <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vermesini engellemek `false` için denetimin özelliğini olarak ayarlayın. <xref:System.Windows.Forms.WebBrowser></span><span class="sxs-lookup"><span data-stu-id="bf7f8-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. <span data-ttu-id="bf7f8-112">Formun oluşturucusunda veya bir <xref:System.Windows.Forms.Form.Load> olay işleyicisinde özelliğiayarlayın.<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A></span><span class="sxs-lookup"><span data-stu-id="bf7f8-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>

     <span data-ttu-id="bf7f8-113">Aşağıdaki kod, komut dosyası nesnesi için form sınıfının kendisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-113">The following code uses the form class itself for the scripting object.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="bf7f8-114">Bileşen nesne modeli (COM), betik nesnesine erişebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="bf7f8-115">Formunuzu com 'a görünür hale getirmek için <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini form sınıfınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. <span data-ttu-id="bf7f8-116">Betik kodunuzun kullanacağı uygulama kodunuzda ortak özellikleri veya yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-116">Implement public properties or methods in your application code that your script code will use.</span></span>

     <span data-ttu-id="bf7f8-117">Örneğin, betik nesnesi için form sınıfını kullanırsanız, form Sınıfınıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. <span data-ttu-id="bf7f8-118">Belirtilen nesnenin ortak özelliklerine ve yöntemlerine erişmek için komut dosyası kodunuzda nesnesinikullanın.`window.external`</span><span class="sxs-lookup"><span data-stu-id="bf7f8-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>

     <span data-ttu-id="bf7f8-119">Aşağıdaki HTML kodu, bir düğme tıklaağından betik nesnesi üzerinde bir yöntemin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="bf7f8-120">Bu kodu, denetimin <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemini kullanarak yüklediğiniz veya <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> denetimin özelliğine atadığınız bir HTML belgesinin Body öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. <span data-ttu-id="bf7f8-121">Betik kodunuzda, uygulama kodunuzun kullanacağı işlevleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-121">Implement functions in your script code that your application code will use.</span></span>

     <span data-ttu-id="bf7f8-122">Aşağıdaki HTML BETIĞI öğesi örnek bir işlev sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="bf7f8-123">Bu kodu, denetimin <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemini kullanarak yüklediğiniz veya <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> denetimin özelliğine atadığınız bir HTML belgesinin baş öğesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. <span data-ttu-id="bf7f8-124">İstemci uygulama kodunuzda betik koduna erişmek için özelliğinikullanın.<xref:System.Windows.Forms.WebBrowser.Document%2A></span><span class="sxs-lookup"><span data-stu-id="bf7f8-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>

     <span data-ttu-id="bf7f8-125">Örneğin, bir düğme <xref:System.Windows.Forms.Control.Click> olay işleyicisine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. <span data-ttu-id="bf7f8-126">DHTML kodunuzda hata ayıklamayı tamamladıktan sonra, <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> <xref:System.Windows.Forms.WebBrowser> denetimin komut dosyası kodu sorunları için hata `true` iletilerini görüntülemesini engellemek için denetimin özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a><span data-ttu-id="bf7f8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf7f8-127">Example</span></span>

<span data-ttu-id="bf7f8-128">Aşağıdaki kod örneği, bu özelliği anlamak için kullanabileceğiniz bir tanıtım uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="bf7f8-129">HTML kodu, ayrı bir HTML dosyasından <xref:System.Windows.Forms.WebBrowser> yüklenmesi yerine <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği aracılığıyla denetime yüklenir.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="bf7f8-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bf7f8-130">Compiling the Code</span></span>

<span data-ttu-id="bf7f8-131">Bu kod şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bf7f8-131">This code requires:</span></span>

- <span data-ttu-id="bf7f8-132">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-132">References to the System and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7f8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf7f8-133">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bf7f8-134">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="bf7f8-134">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
