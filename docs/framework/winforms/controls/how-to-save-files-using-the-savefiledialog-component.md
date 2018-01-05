---
title: "Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme"
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
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70301cd3d357ab90ac6e7ed6d76a902107ef5e4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="0f4e7-102">Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="0f4e7-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="0f4e7-103"><xref:System.Windows.Forms.SaveFileDialog> Bileşeni, dosya sistemi göz atın ve kaydedilecek dosyaları seçmek kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="0f4e7-104">İletişim kutusu, kullanıcı iletişim kutusundaki seçilmiş dosyanın adını ve yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="0f4e7-105">Ancak, aslında dosyaları diske yazmak için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="0f4e7-106">SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0f4e7-106">To save a file using the SaveFileDialog component</span></span>  
  
-   <span data-ttu-id="0f4e7-107">Görüntü **dosyayı Kaydet** iletişim kutusu ve kullanıcı tarafından seçilen dosyanın kaydedileceği bir yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="0f4e7-108">Kullanım <xref:System.Windows.Forms.SaveFileDialog> bileşenin <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="0f4e7-109">Bu yöntem sağlayan bir <xref:System.IO.Stream> nesnesi için yazma.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="0f4e7-110">Kullandığı aşağıdaki örnekte <xref:System.Windows.Forms.DialogResult> dosyasının adını almak için özellik ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="0f4e7-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Yöntemi veya dosyaya yazmak için bir akış sunar.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="0f4e7-112">Aşağıdaki örnekte, var olan bir <xref:System.Windows.Forms.Button> kendisine atanmış bir görüntüyle denetim.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="0f4e7-113">Düğmeye tıkladığınızda bir <xref:System.Windows.Forms.SaveFileDialog> bileşen türü .gif, .jpeg ve .bmp dosyaları tanıyan bir filtre ile örneği.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="0f4e7-114">Bu tür bir dosyayı dosya Kaydet iletişim kutusunda seçili ise, düğmenin resim kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0f4e7-115">Almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği, derlemenizi gerektiren bir ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="0f4e7-116">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="0f4e7-117">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0f4e7-117">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="0f4e7-118">Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> ile denetim kendi <xref:System.Windows.Forms.ButtonBase.Image%2A> özellik türü .gif, .jpeg veya .bmp dosyasına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f4e7-119"><xref:System.Windows.Forms.FileDialog> Sınıfının <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> özelliği (, devralma nedeniyle olduğu parçası <xref:System.Windows.Forms.SaveFileDialog> sınıfı) tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="0f4e7-120">Bu verileri (örneğin, kaydetme ikili biçimi yerine düz metin dosyasında) belirli bir biçimde kaydetmek için kod yazıyorsanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="0f4e7-121">Bu özellik, aşağıdaki örnekte öne çıkan.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-121">This property is featured in the example below.</span></span>  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="0f4e7-122">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-122">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="0f4e7-123">Dosya akışları yazma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0f4e7-124">Gibi belirli denetimleri <xref:System.Windows.Forms.RichTextBox> denetlemek, dosyaları kaydedebilir seçeneğine sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="0f4e7-125">Daha fazla bilgi için MSDN Çevrimiçi Kitaplığı teknik makalenin "SaveFileDialog bileşeni" bölümüne bakın [Windows için önemli kod Forms iletişim kutuları](http://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="0f4e7-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4e7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-126">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="0f4e7-127">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0f4e7-127">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
