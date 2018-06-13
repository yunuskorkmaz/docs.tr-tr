---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536201"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="67859-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="67859-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="67859-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetim birkaç biçimlerinden birinde görüntülediği bilgi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="67859-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="67859-104">Düz metin</span><span class="sxs-lookup"><span data-stu-id="67859-104">Plain text</span></span>  
  
-   <span data-ttu-id="67859-105">Unicode düz metin</span><span class="sxs-lookup"><span data-stu-id="67859-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="67859-106">Zengin metin biçimi (RTF)</span><span class="sxs-lookup"><span data-stu-id="67859-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="67859-107">OLE nesneleri yerine boşluklu RTF</span><span class="sxs-lookup"><span data-stu-id="67859-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="67859-108">OLE nesneleri metinsel gösterimini düz metin</span><span class="sxs-lookup"><span data-stu-id="67859-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="67859-109">Bir dosyayı kaydetmek için arama <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67859-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="67859-110">Aynı zamanda **SaveFile** bir akış için verileri kaydetmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="67859-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="67859-111">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="67859-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="67859-112">Denetimin içeriğini bir dosyaya kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="67859-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="67859-113">Kaydedilecek dosyasının yolunu belirler.</span><span class="sxs-lookup"><span data-stu-id="67859-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="67859-114">Gerçek dünya uygulamada Bunu yapmak için genellikle kullanırsınız <xref:System.Windows.Forms.SaveFileDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="67859-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="67859-115">Genel bir bakış için bkz: [SaveFileDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="67859-115">For an overview, see [SaveFileDialog Component Overview](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="67859-116">Çağrı <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> denetim, kaydedin ve isteğe bağlı olarak bir dosya türünü belirtme.</span><span class="sxs-lookup"><span data-stu-id="67859-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="67859-117">Yalnızca bağımsız değişkeni olarak bir dosya adıyla yöntemini çağırırsanız, dosyayı RTF olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="67859-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="67859-118">Başka bir dosya türü belirtmek için değerini yöntemi çağırma <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması ikinci bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="67859-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="67859-119">Aşağıdaki örnekte yolunu ayarlamak için zengin metin dosyasının konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="67859-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="67859-120">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67859-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="67859-121">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri kullanıcılarla sağlar.</span><span class="sxs-lookup"><span data-stu-id="67859-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="67859-122">Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="67859-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="67859-123">Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67859-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="67859-124">Bir uygulama bir dosya oluşturmak gerekirse, bu uygulama için klasör oluşturma erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="67859-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="67859-125">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="67859-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="67859-126">Dosya zaten varsa, uygulamanın daha düşük ayrıcalık yalnızca yazma erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="67859-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="67859-127">Mümkünse, dağıtım sırasında dosyayı oluşturmak ve yalnızca tek bir dosya için okuma yetkisi vermek yerine, erişim için bir klasör oluşturmak için daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="67859-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="67859-128">Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="67859-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67859-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67859-129">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="67859-130">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="67859-130">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="67859-131">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="67859-131">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
