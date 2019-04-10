---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: faaa48051c80b6dfd330f15f72a38297ff2d1b9f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301886"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c0c79-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c0c79-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c0c79-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, Web bağlantıları görüntüleyebilir, renkli ve altı çizili olarak.</span><span class="sxs-lookup"><span data-stu-id="c0c79-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="c0c79-104">Bağlantıya tıklandığında bağlantı metni belirtilen Web sitesi gösteren bir tarayıcı penceresi açılır kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0c79-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="c0c79-105">RichTextBox denetimi ile bir Web sayfasına bağlantı için</span><span class="sxs-lookup"><span data-stu-id="c0c79-105">To link to a Web page with the RichTextBox control</span></span>  
  
1. <span data-ttu-id="c0c79-106">Ayarlama <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliğine geçerli bir URL içeren bir dize (örneğin, "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="c0c79-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2. <span data-ttu-id="c0c79-107">Emin <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliği `true` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="c0c79-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3. <span data-ttu-id="c0c79-108">Genel yeni bir örneğini oluşturma <xref:System.Diagnostics.Process> nesne.</span><span class="sxs-lookup"><span data-stu-id="c0c79-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4. <span data-ttu-id="c0c79-109">Bir olay işleyicisi için yazma <xref:System.Windows.Forms.RichTextBox.LinkClicked> tarayıcı istediğiniz metni gönderen olay.</span><span class="sxs-lookup"><span data-stu-id="c0c79-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="c0c79-110">Aşağıdaki örnekte <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay bir örneğini belirtilen URL'ye Internet Explorer açılır <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c0c79-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c0c79-111">Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c0c79-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c0c79-112">İçinde arama <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> yöntemi karşılaşırsınız bir <xref:System.Security.SecurityException> yetersiz ayrıcalıklar nedeniyle bir kısmi güven bağlamında kod çalıştırıyorsanız, özel durum.</span><span class="sxs-lookup"><span data-stu-id="c0c79-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="c0c79-113">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c0c79-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     <span data-ttu-id="c0c79-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) İşlemi başlatmalısınız `p`, formunuzu oluşturucuda aşağıdaki deyim ekleyerek yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0c79-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="c0c79-115">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c0c79-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     <span data-ttu-id="c0c79-116">Hemen çalışmaya tamamladıktan sonra oluşturduğunuz işlemi durdurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c0c79-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="c0c79-117">Yukarıda gösterilen koda başvuran, işlemi durdurmak için kodunuzda şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="c0c79-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c0c79-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0c79-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="c0c79-119">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="c0c79-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="c0c79-120">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="c0c79-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
