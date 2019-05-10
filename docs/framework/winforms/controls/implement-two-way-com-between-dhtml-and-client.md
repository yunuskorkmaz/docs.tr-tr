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
ms.openlocfilehash: a31a35257921c6dec6229b5cc3222ee3119c325e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625389"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="6563c-102">Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6563c-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="6563c-103">Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> denetimi mevcut dinamik HTML (DHTML) Web uygulama kodu Windows Forms istemci uygulamalarınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6563c-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="6563c-104">Bu, önemli geliştirme süresini DHTML tabanlı denetimler oluşturma yatırım yapmış ve mevcut kodu yeniden yazmak zorunda kalmadan Windows formlarının zengin kullanıcı arabirimi özelliklerinden yararlanan istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="6563c-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="6563c-105"><xref:System.Windows.Forms.WebBrowser> Denetimi Web sayfasına komut dosyası kodunuzda, istemci uygulaması kodu arasında iki yönlü iletişim uygulamanıza olanak tanır <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> ve <xref:System.Windows.Forms.WebBrowser.Document%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6563c-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="6563c-106">Buna ek olarak, yapılandırabileceğiniz <xref:System.Windows.Forms.WebBrowser> Web denetimleri, diğer denetimleri, uygulamanın formunuzda, DHTML geliştirdikleri gizleme ile sorunsuz bir şekilde blend göstermelerini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6563c-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="6563c-107">Sorunsuz bir şekilde denetimleri karıştırmak için görsel stil ve arka plan rengi formun kalanını eşleşen ve kullanmak görüntülenen sayfa biçimlendirme <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, ve <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> standart tarayıcı özellikleri devre dışı bırakmak için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6563c-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="6563c-108">Windows Forms uygulaması'nda DHTML eklemek için</span><span class="sxs-lookup"><span data-stu-id="6563c-108">To embed DHTML in your Windows Forms application</span></span>  
  
1. <span data-ttu-id="6563c-109">Ayarlama <xref:System.Windows.Forms.WebBrowser> denetimin <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğini `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açma denetimi.</span><span class="sxs-lookup"><span data-stu-id="6563c-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2. <span data-ttu-id="6563c-110">Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> özelliğini `false` önlemek için <xref:System.Windows.Forms.WebBrowser> denetiminin kullanıcı tıkladığında, kısayol menüsünü görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="6563c-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3. <span data-ttu-id="6563c-111">Denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> özelliğini `false` önlemek için <xref:System.Windows.Forms.WebBrowser> kısayol tuşları için yanıt denetimi.</span><span class="sxs-lookup"><span data-stu-id="6563c-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4. <span data-ttu-id="6563c-112">Ayarlama <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> formun Oluşturucusu bir özellik veya <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6563c-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="6563c-113">Aşağıdaki kod, betik oluşturma nesne için form sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6563c-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6563c-114">Bileşen Nesne Modeli (COM) komut dosyası nesnesi erişebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6563c-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="6563c-115">Formunuza COM görünür hale getirmek için ekleme <xref:System.Runtime.InteropServices.ComVisibleAttribute> form sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6563c-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5. <span data-ttu-id="6563c-116">Genel Özellikler veya yöntemler, uygulama kodunuzda betik kodunuzun kullanacağı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6563c-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="6563c-117">Örneğin, betik oluşturma nesne için form sınıfı kullanırsanız, form sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6563c-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6. <span data-ttu-id="6563c-118">Kullanım `window.external` genel özellikleri ve yöntemleri belirtilen nesnenin erişmek için komut dosyası kodunuzda bir nesne.</span><span class="sxs-lookup"><span data-stu-id="6563c-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="6563c-119">Aşağıdaki HTML kod bir düğmeyi tıklatın betik oluşturma nesne üzerinde bir yöntemi çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6563c-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="6563c-120">Bu kodu denetimin kullanarak yükleyen bir HTML belgesi gövde öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atadığınız <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6563c-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7. <span data-ttu-id="6563c-121">Betik kodunuzu uygulama kodunuzun kullanacağı işlevleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6563c-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="6563c-122">Aşağıdaki HTML BETİK öğesi, bir örnek işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6563c-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="6563c-123">Bu kodu denetimin kullanarak yükleyen bir HTML belgesi baş öğesinin içine kopyalayın <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi veya denetimin atadığınız <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6563c-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8. <span data-ttu-id="6563c-124">Kullanım <xref:System.Windows.Forms.WebBrowser.Document%2A> betik kodu istemci uygulama kodunuz içinden erişmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="6563c-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="6563c-125">Örneğin, aşağıdaki kod bir düğme ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6563c-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="6563c-126">Hata ayıklama, DHTML işiniz bittiğinde, denetimin ayarlamak <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> özelliğini `true` önlemek için <xref:System.Windows.Forms.WebBrowser> betik kodu sorunlar için hata iletileri görüntülenmesini denetim.</span><span class="sxs-lookup"><span data-stu-id="6563c-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="6563c-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="6563c-127">Example</span></span>  
 <span data-ttu-id="6563c-128">Aşağıdaki kod örneği, bu özellik anlamak için kullanabileceğiniz bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6563c-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="6563c-129">HTML kod yüklendiği <xref:System.Windows.Forms.WebBrowser> aracılığıyla kontrol <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özelliği yerine ayrı bir HTML dosyasından yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="6563c-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6563c-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6563c-130">Compiling the Code</span></span>  
 <span data-ttu-id="6563c-131">Bu kod gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6563c-131">This code requires:</span></span>  
  
- <span data-ttu-id="6563c-132">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6563c-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6563c-133">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6563c-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6563c-134">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6563c-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6563c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6563c-135">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6563c-136">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="6563c-136">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
