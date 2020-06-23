---
title: 'Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme'
description: Dosya sistemine gözatıp kaydedilecek dosyaları seçmek için SaveFileDialog bileşenini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904409"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="e35be-103">Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e35be-103">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="e35be-104"><xref:System.Windows.Forms.SaveFileDialog>Bileşen, kullanıcıların dosya sistemine gözatmasına ve kaydedilecek dosyaları seçmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35be-104">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="e35be-105">İletişim kutusu, iletişim kutusunda kullanıcının seçtiği dosyanın yolunu ve adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e35be-105">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="e35be-106">Ancak, dosyaları diske gerçekten yazmak için kodu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e35be-106">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="e35be-107">SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="e35be-107">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="e35be-108">**Dosya Kaydet** iletişim kutusunu görüntüleyin ve Kullanıcı tarafından seçilen dosyayı kaydetmek için bir yöntem çağırın.</span><span class="sxs-lookup"><span data-stu-id="e35be-108">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="e35be-109"><xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Dosyayı kaydetmek için bileşenin metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e35be-109">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="e35be-110">Bu yöntem, size <xref:System.IO.Stream> yazabilmenizi sağlayan bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35be-110">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="e35be-111">Aşağıdaki örnek, <xref:System.Windows.Forms.DialogResult> dosyanın adını ve dosyayı kaydetme yöntemini almak için özelliğini kullanır <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="e35be-111">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="e35be-112"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>Yöntemi, size dosyayı yazmak için bir akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e35be-112">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="e35be-113">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> bir görüntüye atanmış bir denetim vardır.</span><span class="sxs-lookup"><span data-stu-id="e35be-113">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="e35be-114">Düğmeye tıkladığınızda bir <xref:System.Windows.Forms.SaveFileDialog> bileşen örneği, Type. gif,. JPEG ve. bmp olan dosyalara izin veren bir filtreyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e35be-114">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="e35be-115">Dosya Kaydet iletişim kutusunda bu türden bir dosya seçiliyse düğmenin görüntüsü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e35be-115">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e35be-116">Özelliği almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> , derlemeniz sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e35be-116">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e35be-117">Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e35be-117">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e35be-118">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e35be-118">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="e35be-119">Örnek, formunuzun <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.ButtonBase.Image%2A> özelliği. gif,. jpeg veya. bmp olan bir dosyaya ayarlanmış bir denetime sahip olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e35be-119">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e35be-120"><xref:System.Windows.Forms.FileDialog>Sınıfın <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> Özelliği (devralma nedeniyle, sınıfın bir parçası olduğu için <xref:System.Windows.Forms.SaveFileDialog> ) tek tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="e35be-120">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="e35be-121">Verileri belirli bir biçimde kaydetmek için kod yazıyorsanız (örneğin, bir dosyayı düz metin ve ikili biçimde kaydetme), bu önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e35be-121">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="e35be-122">Bu özellik aşağıdaki örnekte öne çıkmıştır.</span><span class="sxs-lookup"><span data-stu-id="e35be-122">This property is featured in the example below.</span></span>

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

  <span data-ttu-id="e35be-123">(Visual C# ve Visual C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e35be-123">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="e35be-124">Dosya akışları yazma hakkında daha fazla bilgi için bkz <xref:System.IO.FileStream.BeginWrite%2A> <xref:System.IO.FileStream.Write%2A> . ve.</span><span class="sxs-lookup"><span data-stu-id="e35be-124">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e35be-125">Denetim gibi bazı denetimlerin <xref:System.Windows.Forms.RichTextBox> dosyaları kaydetme yeteneği vardır.</span><span class="sxs-lookup"><span data-stu-id="e35be-125">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="e35be-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e35be-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="e35be-127">SaveFileDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e35be-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
