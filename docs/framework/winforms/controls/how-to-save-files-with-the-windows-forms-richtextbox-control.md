---
title: RichTextBox denetimiyle dosyaları kaydetme
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
ms.openlocfilehash: a87b93a53347aeba54f944b0f4c455aa272ea243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744824"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="a2a05-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a2a05-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="a2a05-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülenen bilgileri birkaç biçimden birinde yazabilir:</span><span class="sxs-lookup"><span data-stu-id="a2a05-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>

- <span data-ttu-id="a2a05-104">Düz metin</span><span class="sxs-lookup"><span data-stu-id="a2a05-104">Plain text</span></span>

- <span data-ttu-id="a2a05-105">Unicode düz metin</span><span class="sxs-lookup"><span data-stu-id="a2a05-105">Unicode plain text</span></span>

- <span data-ttu-id="a2a05-106">Zengin metin biçimi (RTF)</span><span class="sxs-lookup"><span data-stu-id="a2a05-106">Rich-Text Format (RTF)</span></span>

- <span data-ttu-id="a2a05-107">OLE nesneleri yerine boşluklar içeren RTF</span><span class="sxs-lookup"><span data-stu-id="a2a05-107">RTF with spaces in place of OLE objects</span></span>

- <span data-ttu-id="a2a05-108">OLE nesnelerinin metinsel gösterimine sahip düz metin</span><span class="sxs-lookup"><span data-stu-id="a2a05-108">Plain text with a textual representation of OLE objects</span></span>

<span data-ttu-id="a2a05-109">Bir dosyayı kaydetmek için <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a2a05-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="a2a05-110">Verileri bir akışa kaydetmek için **SaveFile** yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2a05-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="a2a05-111">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="a2a05-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="a2a05-112">Denetimin içeriğini bir dosyaya kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="a2a05-112">To save the contents of the control to a file</span></span>

1. <span data-ttu-id="a2a05-113">Kaydedilecek dosyanın yolunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="a2a05-113">Determine the path of the file to be saved.</span></span>

    <span data-ttu-id="a2a05-114">Bunu gerçek dünya uygulamasında yapmak için genellikle <xref:System.Windows.Forms.SaveFileDialog> bileşenini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a2a05-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="a2a05-115">Genel bakış için bkz. [SaveFileDialog Bileşenine Genel Bakış](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a2a05-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="a2a05-116">Kaydedilecek dosyayı ve isteğe bağlı olarak bir dosya türünü belirterek <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a2a05-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="a2a05-117">Yöntemini tek bağımsız değişkeni olarak bir dosya adı ile çağırırsanız, Dosya RTF olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a2a05-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="a2a05-118">Başka bir dosya türü belirtmek için, ikinci bağımsız değişkeni olarak <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması değeri ile yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a2a05-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="a2a05-119">Aşağıdaki örnekte, zengin metin dosyasının konumu için ayarlanan yol **Belgelerim klasörüdür.**</span><span class="sxs-lookup"><span data-stu-id="a2a05-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="a2a05-120">Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2a05-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="a2a05-121">Bu konumun seçilmesi, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a2a05-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="a2a05-122">Aşağıdaki örnekte, <xref:System.Windows.Forms.RichTextBox> denetimi zaten eklenmiş bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a2a05-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>

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
    > <span data-ttu-id="a2a05-123">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2a05-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="a2a05-124">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için erişim oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2a05-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="a2a05-125">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a2a05-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="a2a05-126">Dosya zaten mevcutsa, uygulamanın daha küçük bir ayrıcalık yalnızca yazma erişimine ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="a2a05-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="a2a05-127">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve bir klasör için erişim oluşturmak yerine yalnızca tek bir dosyaya okuma erişimi verilmesi daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="a2a05-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="a2a05-128">Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="a2a05-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2a05-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2a05-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="a2a05-130">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="a2a05-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="a2a05-131">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="a2a05-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
