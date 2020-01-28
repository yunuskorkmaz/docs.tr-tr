---
title: LinkLabel denetimiyle bir nesne veya Web sayfasına bağlantı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 1669a9d6aba39b02d228c735701ca4e31c8f8291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745212"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="0ca3e-102">Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama</span><span class="sxs-lookup"><span data-stu-id="0ca3e-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="0ca3e-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi, formunuzda Web stili bağlantılar oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="0ca3e-104">Bağlantıya tıklandığında, bağlantının ziyaret edildiğini göstermek için rengini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="0ca3e-105">Rengi değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms LinkLabel denetiminin görünümünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="0ca3e-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="0ca3e-106">Başka bir forma bağlama</span><span class="sxs-lookup"><span data-stu-id="0ca3e-106">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="0ca3e-107">LinkLabel denetimiyle başka bir forma bağlamak için</span><span class="sxs-lookup"><span data-stu-id="0ca3e-107">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="0ca3e-108"><xref:System.Windows.Forms.LinkLabel.Text%2A> özelliğini uygun bir başlık olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="0ca3e-109">Başlığın hangi kısmının bağlantı olarak belirtileyeceğini öğrenmek için <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="0ca3e-110">Nasıl belirtildiği, bağlantı etiketinin görünümle ilgili özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="0ca3e-111"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> değeri iki sayı içeren bir <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> nesnesi ile temsil edilir, başlangıç karakterinin konumunu ve karakter sayısını.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="0ca3e-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliği, Özellikler penceresi veya kod içinde aşağıdakine benzer bir şekilde ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="0ca3e-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

    ```vb
    ' In this code example, the link area has been set to begin
    ' at the first character and extend for eight characters.
    ' You may need to modify this based on the text entered in Step 1.
    LinkLabel1.LinkArea = New LinkArea(0, 8)
    ```

    ```csharp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1.LinkArea = new LinkArea(0,8);
    ```

    ```cpp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1->LinkArea = LinkArea(0,8);
    ```

3. <span data-ttu-id="0ca3e-113"><xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyicisinde, projede başka bir form açmak için <xref:System.Windows.Forms.Form.Show%2A> metodunu çağırın ve <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0ca3e-114"><xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> sınıfının bir örneği, tıklanan <xref:System.Windows.Forms.LinkLabel> denetimine bir başvuru taşır, bu nedenle `sender` nesnesini dönüştürmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

    ```vb
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       ' Show another form.
       Dim f2 As New Form()
       f2.Show
       LinkLabel1.LinkVisited = True
    End Sub
    ```

    ```csharp
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       // Show another form.
       Form f2 = new Form();
       f2.Show();
       linkLabel1.LinkVisited = true;
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          // Show another form.
          Form ^ f2 = new Form();
          f2->Show();
          linkLabel1->LinkVisited = true;
       }
    ```

## <a name="linking-to-a-web-page"></a><span data-ttu-id="0ca3e-115">Bir Web sayfasına bağlanma</span><span class="sxs-lookup"><span data-stu-id="0ca3e-115">Linking to a Web Page</span></span>

<span data-ttu-id="0ca3e-116"><xref:System.Windows.Forms.LinkLabel> denetimi, varsayılan tarayıcıyla bir Web sayfası göstermek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="0ca3e-117">Internet Explorer 'ı başlatmak ve LinkLabel denetimiyle bir Web sayfasına bağlantı sağlamak için</span><span class="sxs-lookup"><span data-stu-id="0ca3e-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="0ca3e-118"><xref:System.Windows.Forms.LinkLabel.Text%2A> özelliğini uygun bir başlık olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="0ca3e-119">Başlığın hangi kısmının bağlantı olarak belirtileyeceğini öğrenmek için <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="0ca3e-120"><xref:System.Windows.Forms.LinkLabel.LinkClicked> olay işleyicisinde, özel durum işleme bloğunun ortasında, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> özelliğini `true` olarak ayarlayan ikinci bir yordamı çağırın ve varsayılan tarayıcıyı bir URL ile başlatmak için <xref:System.Diagnostics.Process.Start%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="0ca3e-121"><xref:System.Diagnostics.Process.Start%2A> yöntemini kullanmak için, <xref:System.Diagnostics?displayProperty=nameWithType> ad alanına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0ca3e-122">Aşağıdaki kod, kısmi güven ortamında (örneğin, paylaşılan bir sürücüde) çalışıyorsa, `VisitLink` yöntemi çağrıldığında JıT derleyicisi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="0ca3e-123">`System.Diagnostics.Process.Start` bildiri başarısız olan bağlantı isteğine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="0ca3e-124">`VisitLink` yöntemi çağrıldığında özel durum yakalanarak, aşağıdaki kod JıT derleyicisi başarısız olursa hatanın düzgün şekilde işleneceğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

    ```vb
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       Try
          VisitLink()
       Catch ex As Exception
          ' The error message
          MessageBox.Show("Unable to open link that was clicked.")
       End Try
    End Sub

    Sub VisitLink()
       ' Change the color of the link text by setting LinkVisited
       ' to True.
       LinkLabel1.LinkVisited = True
       ' Call the Process.Start method to open the default browser
       ' with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com")
    End Sub
    ```

    ```csharp
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       try
       {
          VisitLink();
       }
       catch (Exception ex )
       {
          MessageBox.Show("Unable to open link that was clicked.");
       }
    }

    private void VisitLink()
    {
       // Change the color of the link text by setting LinkVisited
       // to true.
       linkLabel1.LinkVisited = true;
       //Call the Process.Start method to open the default browser
       //with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com");
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          try
          {
             VisitLink();
          }
          catch (Exception ^ ex)
          {
             MessageBox::Show("Unable to open link that was clicked.");
          }
       }
    private:
       void VisitLink()
       {
          // Change the color of the link text by setting LinkVisited
          // to true.
          linkLabel1->LinkVisited = true;
          // Call the Process.Start method to open the default browser
          // with a URL:
          System::Diagnostics::Process::Start("http://www.microsoft.com");
       }
    ```

## <a name="see-also"></a><span data-ttu-id="0ca3e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0ca3e-126">LinkLabel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ca3e-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="0ca3e-127">Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0ca3e-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="0ca3e-128">LinkLabel Denetimi</span><span class="sxs-lookup"><span data-stu-id="0ca3e-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
