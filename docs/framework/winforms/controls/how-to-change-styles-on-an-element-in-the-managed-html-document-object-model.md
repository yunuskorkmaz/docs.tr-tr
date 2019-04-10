---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 804041991199dd2722e3a0f38800bafd8933bbab
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333671"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="b4c6d-102">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde Bir Öğedeki Stilleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b4c6d-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>

<span data-ttu-id="b4c6d-103">Bir belge ve onun öğelerine görünümünü kontrol etmek için HTML stillerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <xref:System.Windows.Forms.HtmlDocument> <span data-ttu-id="b4c6d-104">ve <xref:System.Windows.Forms.HtmlElement> Destek <xref:System.Windows.Forms.HtmlElement.Style%2A> stili dizeler aşağıdaki biçimde ele özellikleri:</span><span class="sxs-lookup"><span data-stu-id="b4c6d-104">and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>

`name1:value1;...;nameN:valueN;`

<span data-ttu-id="b4c6d-105">İşte bir `DIV` bir stil dizesiyle kalın Arial ve tüm metin yazı tipini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="b4c6d-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

<span data-ttu-id="b4c6d-106">Düzenleme stilleri kullanarak sorunu <xref:System.Windows.Forms.HtmlElement.Style%2A> özelliği ekleyin ve dizesi bağımsız stil ayarları kaldırmak için hantal kanıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="b4c6d-107">Örneğin, karmaşık bir yordam, önceki metni italik kullanıcı imleci üzerine konumlandırır. her işleme olacak `DIV`ve imleci ayrıldığında kapalı italik yap `DIV`.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="b4c6d-108">Çok sayıda stilleri bu şekilde işlemek istiyorsanız zaman bir sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>

<span data-ttu-id="b4c6d-109">Aşağıdaki yordam, HTML belgeleri ve öğeleri stilleri kolayca yönetmek için kullanabileceğiniz kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="b4c6d-110">Yordamı, yeni proje oluşturma ve bir forma denetim ekleme gibi Windows Forms'da temel görevleri gerçekleştirme bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>

### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="b4c6d-111">Bir Windows Forms uygulamasında stil değişikliklerini işlemek için</span><span class="sxs-lookup"><span data-stu-id="b4c6d-111">To process style changes in a Windows Forms application</span></span>

1. <span data-ttu-id="b4c6d-112">Yeni bir Windows Forms projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-112">Create a new Windows Forms project.</span></span>

2. <span data-ttu-id="b4c6d-113">Programlama diliniz için uygun uzantısında bitiş yeni bir sınıf dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>

3. <span data-ttu-id="b4c6d-114">Kopyalama `StyleGenerator` sınıfı dosyasına kod bu konunun Örnek bölümünde sınıfı ve kodu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>

4. <span data-ttu-id="b4c6d-115">Aşağıdaki HTML'yi Test.htm adlı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-115">Save the following HTML to a file named Test.htm.</span></span>

    ```html
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

5. <span data-ttu-id="b4c6d-116">Ekleme bir <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1` projenizin ana formu için.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>

6. <span data-ttu-id="b4c6d-117">Projenizin kod dosyasına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-117">Add the following code to your project's code file.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="b4c6d-118">Emin `webBrowser1_DocumentCompleted` olay işleyicisi için bir dinleyici olarak yapılandırıldığında <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="b4c6d-119">Visual Studio'da çift tıklayarak <xref:System.Windows.Forms.WebBrowser> denetimi; bir metin düzenleyicisinde dinleyiciyi programlı bir şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7. <span data-ttu-id="b4c6d-120">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-120">Run the project.</span></span> <span data-ttu-id="b4c6d-121">İmlecinizi ilk çalıştırma `DIV` kod etkilerini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4c6d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4c6d-122">Example</span></span>  
 <span data-ttu-id="b4c6d-123">Aşağıdaki kod örneği için tam kod gösterilir `StyleGenerator` varolan bir stili değeri ayrıştırır, sınıf, destekler ekleme, değiştirme ve kaldırma stiller ve istenen değişiklikler yeni bir stil değeriyle döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b4c6d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4c6d-124">See also</span></span>

- <xref:System.Windows.Forms.HtmlElement>
