---
title: "Nasıl Yapılır: OpenFileDialog Bileşenini Kullanarak Dosyaları Açma"
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
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fabe176ade1ae94a20100162ab7ab6fadfb2999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="ed553-102">Nasıl Yapılır: OpenFileDialog Bileşenini Kullanarak Dosyaları Açma</span><span class="sxs-lookup"><span data-stu-id="ed553-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="ed553-103"><xref:System.Windows.Forms.OpenFileDialog> Bileşeni, kullanıcıların ağ üzerindeki herhangi bir bilgisayar veya bilgisayarlarını klasörleri bulun ve açmak için bir veya daha fazla dosya seçin sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed553-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="ed553-104">İletişim kutusu, iletişim kutusunda seçili kullanıcı dosyasının adını ve yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed553-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="ed553-105">Kullanıcı açılması için dosyanın seçtikten sonra dosyayı açma mekanizması için iki yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="ed553-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="ed553-106">Dosya akışları ile çalışmayı tercih ederseniz örneği oluşturabilirsiniz <xref:System.IO.StreamReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ed553-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="ed553-107">Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> seçilen dosyayı açmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ed553-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="ed553-108">Aşağıdaki ilk örnekte içerir bir <xref:System.Security.Permissions.FileIOPermission> ("güvenlik Not" aşağıda açıklandığı gibi) izni denetimi ancak dosya adına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed553-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="ed553-109">Yerel makine, Intranet ve Internet bölgelerinden bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed553-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="ed553-110">İkinci yöntem de mu bir <xref:System.Security.Permissions.FileIOPermission> izni denetimi, ancak daha iyi Intranet veya Internet bölgelerde uygulamalar için uygun.</span><span class="sxs-lookup"><span data-stu-id="ed553-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="ed553-111">OpenFileDialog bileşenini kullanarak bir akış bir dosyayı açmak için</span><span class="sxs-lookup"><span data-stu-id="ed553-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="ed553-112">Görüntü **Dosya Aç** iletişim kutusu ve kullanıcı tarafından seçilen dosyayı açmak için bir yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ed553-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="ed553-113">Bir yaklaşım ise kullanılacak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Dosya Aç iletişim kutusu görüntülemek ve bir örneğini kullanması için yöntem <xref:System.IO.StreamReader> dosyayı açmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ed553-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="ed553-114">Kullandığı aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> bir örneğini açmak için olay işleyicisini <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="ed553-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="ed553-115">Bir dosya seçilen ve kullanıcı olduğunda tıklar **Tamam**, iletişim kutusunda seçili dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="ed553-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="ed553-116">Bu durumda, içeriği yalnızca dosya akışı Okunmuş göstermek için bir ileti kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ed553-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ed553-117">Almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği, derlemenizi gerektiren bir ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ed553-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ed553-118">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="ed553-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ed553-119">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ed553-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="ed553-120">Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetim ve bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="ed553-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="ed553-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed553-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ed553-122">Dosya akışları okuma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed553-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="ed553-123">OpenFileDialog bileşenini kullanarak bir dosya olarak bir dosyayı açmak için</span><span class="sxs-lookup"><span data-stu-id="ed553-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="ed553-124">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="ed553-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="ed553-125"><xref:System.Windows.Forms.OpenFileDialog> Bileşenin <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını oluşturan bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed553-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="ed553-126">Bu bayt okuma bir akış verin.</span><span class="sxs-lookup"><span data-stu-id="ed553-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="ed553-127">Aşağıdaki örnekte bir <xref:System.Windows.Forms.OpenFileDialog> bileşen örneği yalnızca dosya adı uzantısına sahip dosyalar seçmesine izin verme "imleç" filtre da ile`.cur`.</span><span class="sxs-lookup"><span data-stu-id="ed553-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="ed553-128">Varsa bir`.cur` dosya seçilmişse, formun imleç seçili imleci ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ed553-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ed553-129">Çağrılacak <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> , derlemenizi gerektirdiğine ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ed553-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ed553-130">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="ed553-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ed553-131">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ed553-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="ed553-132">Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="ed553-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     <span data-ttu-id="ed553-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed553-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ed553-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed553-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="ed553-135">OpenFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ed553-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
