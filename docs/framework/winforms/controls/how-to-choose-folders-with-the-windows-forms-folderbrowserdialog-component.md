---
title: 'Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046130"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="a4d8a-102">Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme</span><span class="sxs-lookup"><span data-stu-id="a4d8a-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="a4d8a-103">Genellikle, oluşturduğunuz Windows uygulamalarında, bir dosya kümesini kaydetmek için kullanıcılardan bir klasör seçmesini istemek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="a4d8a-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni bu görevi kolayca gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="a4d8a-105">FolderBrowserDialog Bileşeni ile klasörleri seçmek için</span><span class="sxs-lookup"><span data-stu-id="a4d8a-105">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="a4d8a-106">Bir yordamda, iletişim kutusunun nasıl <xref:System.Windows.Forms.FolderBrowserDialog> kapatıldığını görmek <xref:System.Windows.Forms.Form.DialogResult%2A> ve <xref:System.Windows.Forms.FolderBrowserDialog> bileşen <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliğinin değerini almak için bileşenin özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="a4d8a-107">İletişim kutusunun ağaç görünümünde görünecek en üstteki klasörü ayarlamanız gerekirse, <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> <xref:System.Environment.SpecialFolder> sabit listesinin bir üyesini alan özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="a4d8a-108">Ayrıca, klasör tarayıcısı ağaç görünümünün <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> en üstünde görünen metin dizesini belirten özelliğini de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="a4d8a-109">Aşağıdaki örnekte, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'da bir proje oluştururken olduğu gibi bir klasörü seçmek için kullanılır ve dosyayı kaydetmek için bir klasör seçmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="a4d8a-110">Bu örnekte, klasör adı form üzerindeki bir <xref:System.Windows.Forms.TextBox> denetimde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="a4d8a-111">Bu, bir denetim gibi düzenlenebilir bir alana, kullanıcıların bir hata durumunda veya başka sorunlar durumunda <xref:System.Windows.Forms.TextBox> kendi seçimini düzenleyebilmeleri için, konumunu bir şekilde yerleştirmek iyi bir fikir olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="a4d8a-112">Bu örnekte <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.TextBox> , bir form ve bir denetim içeren bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

    ```vb
    Public Sub ChooseFolder()
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then
            TextBox1.Text = FolderBrowserDialog1.SelectedPath
        End If
    End Sub
    ```

    ```csharp
    public void ChooseFolder()
    {
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)
        {
            textBox1.Text = folderBrowserDialog1.SelectedPath;
        }
    }
    ```

    ```cpp
    public:
       void ChooseFolder()
       {
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)
          {
             textBox1->Text = folderBrowserDialog1->SelectedPath;
          }
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="a4d8a-113">Bu sınıfı kullanmak için, derlemeniz, <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess> numaralandırmanın bir parçası olan özelliği tarafından verilen bir ayrıcalık düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="a4d8a-114">Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="a4d8a-115">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a4d8a-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="a4d8a-116">Dosyaların nasıl kaydedileceği hakkında bilgi için bkz [. nasıl yapılır: Dosyaları SaveFileDialog bileşenini](how-to-save-files-using-the-savefiledialog-component.md)kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4d8a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d8a-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="a4d8a-118">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a4d8a-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="a4d8a-119">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a4d8a-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
