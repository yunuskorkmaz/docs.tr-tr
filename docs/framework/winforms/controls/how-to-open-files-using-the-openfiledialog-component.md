---
title: 'Nasıl yapılır: OpenFileDialog bileşenini kullanarak dosyaları açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678817"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="e2273-102">Nasıl yapılır: OpenFileDialog bileşenini kullanarak dosyaları açma</span><span class="sxs-lookup"><span data-stu-id="e2273-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="e2273-103"><xref:System.Windows.Forms.OpenFileDialog> Bileşen, kullanıcıları, bilgisayarları veya ağ üzerindeki herhangi bir bilgisayarda klasörleri ve açmak için bir veya daha fazla dosya seçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2273-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="e2273-104">İletişim kutusu iletişim kutusunda seçili kullanıcı dosyasının adını ve yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2273-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="e2273-105">Kullanıcı açılacak dosyayı seçtikten sonra dosyanın açılış mekanizması için iki yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="e2273-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="e2273-106">Dosya akışları ile çalışmayı tercih ederseniz, bir örneğini oluşturabilirsiniz <xref:System.IO.StreamReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2273-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="e2273-107">Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> seçili dosyayı açmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2273-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="e2273-108">İlk örnek içeren bir <xref:System.Security.Permissions.FileIOPermission> izni denetimi ("güvenlik Not" aşağıda açıklandığı gibi), ancak dosya adına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2273-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="e2273-109">Yerel makine, Intranet ve Internet bölgelerinden bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2273-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="e2273-110">İkinci yöntem aynı zamanda mu bir <xref:System.Security.Permissions.FileIOPermission> izni olup olmadığını denetler, ancak daha iyi uygulamalar Intranet veya Internet bölgeleri için uygun.</span><span class="sxs-lookup"><span data-stu-id="e2273-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="e2273-111">OpenFileDialog bileşenini kullanarak bir akış olarak bir dosyayı açmak için</span><span class="sxs-lookup"><span data-stu-id="e2273-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="e2273-112">Görüntü **Dosya Aç** iletişim kutusu ve kullanıcının seçtiği dosyayı açmak için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="e2273-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="e2273-113">Bir yaklaşım ise kullanılacak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Dosya Aç iletişim kutusunu görüntülemek ve kullanmak için yöntem <xref:System.IO.StreamReader> dosyayı açmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e2273-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="e2273-114">Kullanan aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> örneğini açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e2273-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="e2273-115">Seçilen ve kullanıcı bir dosya olduğunda tıkladığında **Tamam**, iletişim kutusunda seçili dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="e2273-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="e2273-116">Bu durumda, içeriği yalnızca dosya akışı Okunmuş olduğunu göstermek için bir ileti kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2273-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e2273-117">Alınacak veya ayarlanacak <xref:System.Windows.Forms.FileDialog.FileName%2A> özellik, derlemenizin gerektirir ayrıcalık düzeyi verilmiş tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2273-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e2273-118">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="e2273-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e2273-119">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e2273-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="e2273-120">Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi ve bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e2273-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="e2273-121">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e2273-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e2273-122">Dosya akışları okuma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2273-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="e2273-123">OpenFileDialog bileşenini kullanarak bir dosya olarak bir dosyayı açmak için</span><span class="sxs-lookup"><span data-stu-id="e2273-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="e2273-124">Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dosyayı açmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2273-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="e2273-125"><xref:System.Windows.Forms.OpenFileDialog> Bileşenin <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi compose dosyası bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2273-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="e2273-126">Bir akış okumak için size bu bayt.</span><span class="sxs-lookup"><span data-stu-id="e2273-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="e2273-127">Aşağıdaki örnekte bir <xref:System.Windows.Forms.OpenFileDialog> bileşen örneği ile yalnızca dosya adı uzantısına sahip dosyaları seçmesine izin verme "imleç" filtre da`.cur`.</span><span class="sxs-lookup"><span data-stu-id="e2273-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="e2273-128">Varsa bir`.cur` dosyası seçilmişse, formun imleç seçili imleci ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e2273-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e2273-129">Çağrılacak <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> , derlemenizin gerektirdiğine ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2273-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e2273-130">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="e2273-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e2273-131">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e2273-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="e2273-132">Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e2273-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
     <span data-ttu-id="e2273-133">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e2273-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e2273-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2273-134">See also</span></span>
- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="e2273-135">OpenFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e2273-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
