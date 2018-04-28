---
title: 'Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f449d026cb3205081fba79e0db87fb04ea3b7211
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="23390-102">Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="23390-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="23390-103">Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> denetim Windows Forms istemci uygulamalarınızı varolan dinamik HTML (DHTML) Web uygulama kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="23390-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="23390-104">DHTML tabanlı denetimler oluşturma önemli geliştirme zamanı yatırım yaptıysanız ve var olan kodu yeniden yazmaya gerek kalmadan Windows Forms zengin bir kullanıcı arabirimi özelliklerini yararlanmak istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="23390-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="23390-105"><xref:System.Windows.Forms.WebBrowser> Denetimi yapmanıza izin verir, istemci uygulaması kodu Web sayfası komut dosyası kodu aracılığıyla arasında iki yönlü iletişim uygulamanıza <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> ve <xref:System.Windows.Forms.WebBrowser.Document%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="23390-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="23390-106">Ayrıca, yapılandırabileceğiniz <xref:System.Windows.Forms.WebBrowser> böylece Web denetimleri DHTML uygulamalarının gizleme uygulama formunuzda diğer denetimleri ile sorunsuz bir şekilde blend denetim.</span><span class="sxs-lookup"><span data-stu-id="23390-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="23390-107">Arka plan rengi ve görsel stil formun kalanını eşleşmesi kullanın, görüntülenen sayfa sorunsuz bir şekilde denetimleri blend biçiminde <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, ve <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> standart tarayıcı özellikleri devre dışı bırakmak için özellikler.</span><span class="sxs-lookup"><span data-stu-id="23390-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="23390-108">Windows Forms uygulaması'nda DHTML eklemek için</span><span class="sxs-lookup"><span data-stu-id="23390-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="23390-109">Ayarlama <xref:System.Windows.Forms.WebBrowser> denetimin <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açmasını denetim.</span><span class="sxs-lookup"><span data-stu-id="23390-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="23390-110">Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> kullanıcı tıklattığında Denetimi'nin kısayol menüsünü görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="23390-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="23390-111">Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> kısayol tuşları yanıt denetimi.</span><span class="sxs-lookup"><span data-stu-id="23390-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="23390-112">Ayarlama <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> formun Oluşturucusu özelliğinde veya <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="23390-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="23390-113">Aşağıdaki kod komut dosyası nesnesi için form sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="23390-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23390-114">Bileşen Nesne Modeli (COM) komut dosyası nesnesi erişebilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="23390-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="23390-115">Formunuz COM görünür yapmak için add <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği form sınıfı.</span><span class="sxs-lookup"><span data-stu-id="23390-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="23390-116">Ortak özellikler ve yöntemler uygulama kodunuzda betik kodunuzu kullanacağı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="23390-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="23390-117">Örneğin, komut dosyası nesne için form sınıfı kullanırsanız, form sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="23390-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="23390-118">Kullanım `window.external` genel özellikleri ve yöntemleri belirtilen nesnenin erişmek için komut dosyası kodunuzda nesnesi.</span><span class="sxs-lookup"><span data-stu-id="23390-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="23390-119">Aşağıdaki HTML kodu bir düğmesini tıklatın komut dosyası nesnesinde bir yöntem çağrısı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23390-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="23390-120">Bu kodu bir HTML belgesinin denetimin kullanarak yük gövde öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atamak <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="23390-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="23390-121">İşlevler betik kodunuzu, uygulama kodunuzda kullanacağınız uygulayın.</span><span class="sxs-lookup"><span data-stu-id="23390-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="23390-122">Aşağıdaki HTML komut dosyası öğesi, bir örnek işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="23390-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="23390-123">Bu kodu denetimin kullanarak yük bir HTML belgesinin HEAD öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atamak <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="23390-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="23390-124">Kullanım <xref:System.Windows.Forms.WebBrowser.Document%2A> kod istemci uygulama kodunuzdan erişmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="23390-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="23390-125">Örneğin, bir düğmeye aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="23390-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="23390-126">Hata ayıklama, DHTML işiniz bittiğinde, denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> özelliğine `true` önlemek için <xref:System.Windows.Forms.WebBrowser> komut dosyası kodu sorunları için hata iletileri görüntüleme denetimi.</span><span class="sxs-lookup"><span data-stu-id="23390-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="23390-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="23390-127">Example</span></span>  
 <span data-ttu-id="23390-128">Aşağıdaki tam kod örneği, bu özellik anlamak için kullanabileceğiniz bir tanıtım uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="23390-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="23390-129">HTML kod yüklenen <xref:System.Windows.Forms.WebBrowser> aracılığıyla kontrol <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> ayrı bir HTML dosyasından yüklenen yerine özelliği.</span><span class="sxs-lookup"><span data-stu-id="23390-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23390-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="23390-130">Compiling the Code</span></span>  
 <span data-ttu-id="23390-131">Bu kodu gerektirir:</span><span class="sxs-lookup"><span data-stu-id="23390-131">This code requires:</span></span>  
  
-   <span data-ttu-id="23390-132">Sistem ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="23390-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="23390-133">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="23390-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="23390-134">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23390-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="23390-135">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="23390-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23390-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23390-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="23390-137">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="23390-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
