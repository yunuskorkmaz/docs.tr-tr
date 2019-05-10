---
title: 'Nasıl yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 933e049f825bcc8f2afef914f810b52c1cf51245
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638300"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="7a29a-102">Nasıl yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="7a29a-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="7a29a-103"><xref:System.Windows.Forms.SaveFileDialog> Bileşen, dosya sistemi ve kaydedilecek dosyaları seçmek kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a29a-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="7a29a-104">İletişim kutusu iletişim kutusunda kullanıcının seçtiği dosya adını ve yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7a29a-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="7a29a-105">Ancak, gerçekte dosyaları diske yazmak için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a29a-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="7a29a-106">SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="7a29a-106">To save a file using the SaveFileDialog component</span></span>  
  
- <span data-ttu-id="7a29a-107">Görüntü **dosyayı Kaydet** iletişim kutusu ve kullanıcının seçtiği dosyayı kaydetmek için bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="7a29a-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="7a29a-108">Kullanım <xref:System.Windows.Forms.SaveFileDialog> bileşenin <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> dosyayı kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a29a-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="7a29a-109">Bu yöntem size bir <xref:System.IO.Stream> nesne için yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a29a-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="7a29a-110">Kullanan aşağıdaki örnekte <xref:System.Windows.Forms.DialogResult> dosyasının adını almak için özellik ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dosyayı kaydetmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a29a-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="7a29a-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Yöntemi dosyaya yazmak için bir akış sunar.</span><span class="sxs-lookup"><span data-stu-id="7a29a-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="7a29a-112">Aşağıdaki örnekte bir <xref:System.Windows.Forms.Button> kendisine atanmış bir görüntü içeren denetim.</span><span class="sxs-lookup"><span data-stu-id="7a29a-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="7a29a-113">Düğmeye tıkladığınızda bir <xref:System.Windows.Forms.SaveFileDialog> bileşen türü .gif, .jpeg ve .bmp dosyaları izin veren bir filtre ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7a29a-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="7a29a-114">Bu tür bir dosyayı dosya Kaydet iletişim kutusunda seçili ise, düğmenin görüntü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7a29a-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7a29a-115">Alınacak veya ayarlanacak <xref:System.Windows.Forms.FileDialog.FileName%2A> özellik, derlemenizin gerektirir ayrıcalık düzeyi verilmiş tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7a29a-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7a29a-116">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="7a29a-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="7a29a-117">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7a29a-117">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="7a29a-118">Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimini kendi <xref:System.Windows.Forms.ButtonBase.Image%2A> özellik türü .gif, .jpeg veya .bmp dosyasına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7a29a-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a29a-119"><xref:System.Windows.Forms.FileDialog> Sınıfın <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> özelliği (, devralma nedeniyle parçası olan <xref:System.Windows.Forms.SaveFileDialog> sınıfı) bir tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a29a-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="7a29a-120">(Örneğin, kaydetme ikili biçimi yerine düz metin dosyasında) belirli bir biçimdeki verileri kaydetmek için kod yazıyorsanız, bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7a29a-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="7a29a-121">Bu özellik, aşağıdaki örnekte'öne çıkan.</span><span class="sxs-lookup"><span data-stu-id="7a29a-121">This property is featured in the example below.</span></span>  
  
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
  
     <span data-ttu-id="7a29a-122">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7a29a-122">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="7a29a-123">Dosya akışları yazma hakkında daha fazla bilgi için bkz. <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a29a-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a29a-124">Gibi belirli denetimleri <xref:System.Windows.Forms.RichTextBox> denetlemek, dosyaları Kaydet seçeneğine sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a29a-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="7a29a-125">Daha fazla bilgi için MSDN çevrimiçi kitaplığındaki teknik makalenin "SaveFileDialog bileşeni" bölümüne bakın. [Windows için temel kod formları iletişim kutularını](https://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="7a29a-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](https://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a29a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a29a-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="7a29a-127">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="7a29a-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
