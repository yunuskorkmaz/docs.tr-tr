---
title: "Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme"
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
helpviewer_keywords: managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968dd4210e13e301ba2f0ca24617df23706cefc0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="18e46-102">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="18e46-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="18e46-103">Bir belge ve öğeleri görünümünü denetlemek için HTML stilleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="18e46-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="18e46-104"><xref:System.Windows.Forms.HtmlDocument>ve <xref:System.Windows.Forms.HtmlElement> Destek <xref:System.Windows.Forms.HtmlElement.Style%2A> stili dizeleri aşağıdaki biçimde ele özellikleri:</span><span class="sxs-lookup"><span data-stu-id="18e46-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="18e46-105">Burada bir `DIV` bir stil dizesiyle kalın Arial ve tüm metnin yazı tipini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="18e46-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="18e46-106">Düzenleme stilleri kullanarak sorun <xref:System.Windows.Forms.HtmlElement.Style%2A> özelliktir ekleyin ve tek tek stil ayarlarını dizeden kaldırmak için sıkıcı kanıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18e46-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="18e46-107">Örneğin, karmaşık bir yordam, önceki metni italik üzerinden imleci kullanıcı konumlandırır her işlemek olacak `DIV`ve imleci ayrıldığında kapalı italik yapın `DIV`.</span><span class="sxs-lookup"><span data-stu-id="18e46-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="18e46-108">Çok sayıda stilleri bu şekilde işlemek gerekiyorsa zaman bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="18e46-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="18e46-109">Aşağıdaki yordam kolayca HTML belgeleri ve öğeleri stilleri düzenlemek için kullanabileceğiniz kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="18e46-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="18e46-110">Yordam için Windows Forms'ta yeni proje oluşturma ve bir forma denetim ekleme gibi temel görevleri gerçekleştirme bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18e46-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="18e46-111">Stil işlemek için bir Windows Forms uygulamasında değiştirir.</span><span class="sxs-lookup"><span data-stu-id="18e46-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="18e46-112">Yeni bir Windows Forms projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="18e46-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="18e46-113">Programlama diliniz için uygun uzantısında bitiş yeni bir sınıf dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="18e46-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="18e46-114">Kopya `StyleGenerator` sınıfı dosyasına kodunu örnek bölümünde bu konu, sınıf ve kod kaydedin.</span><span class="sxs-lookup"><span data-stu-id="18e46-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="18e46-115">Aşağıdaki HTML Test.htm adlı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="18e46-115">Save the following HTML to a file named Test.htm.</span></span>  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  <span data-ttu-id="18e46-116">Ekleme bir <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1` projenizin ana formuna.</span><span class="sxs-lookup"><span data-stu-id="18e46-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="18e46-117">Projenizin kod dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="18e46-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="18e46-118">Emin `webBrowser1_DocumentCompleted` olay işleyicisi için bir dinleyici olarak yapılandırılmış <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="18e46-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="18e46-119">İçinde [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], çift <xref:System.Windows.Forms.WebBrowser> denetlemek; bir metin düzenleyicisinde dinleyicisini programlı olarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="18e46-119">In [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="18e46-120">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="18e46-120">Run the project.</span></span> <span data-ttu-id="18e46-121">İmleç ilk çalıştırma `DIV` kodun etkilerini izlemek için.</span><span class="sxs-lookup"><span data-stu-id="18e46-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18e46-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="18e46-122">Example</span></span>  
 <span data-ttu-id="18e46-123">Aşağıdaki kod örneği için tam kodu gösterir `StyleGenerator` var olan bir stil değeri ayrıştırır, sınıf destekler ekleme, değiştirme ve kaldırma stilleri ve istenen değişiklikleri ile yeni bir stil değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="18e46-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18e46-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18e46-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
