---
title: FolderBrowserDialog Bileşeni ile klasörleri seçme
description: Kullanıcıların bir klasör seçmesini istemek için oluşturduğunuz Windows uygulamalarında Windows Forms FolderBrowserDialog bileşenini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903681"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="b5673-103">Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme</span><span class="sxs-lookup"><span data-stu-id="b5673-103">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="b5673-104">Genellikle, oluşturduğunuz Windows uygulamalarında, bir dosya kümesini kaydetmek için kullanıcılardan bir klasör seçmesini istemek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="b5673-104">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="b5673-105">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni bu görevi kolayca gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b5673-105">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="b5673-106">FolderBrowserDialog Bileşeni ile klasörleri seçmek için</span><span class="sxs-lookup"><span data-stu-id="b5673-106">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="b5673-107">Bir yordamda, <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.Form.DialogResult%2A> iletişim kutusunun nasıl kapatıldığını görmek ve bileşen özelliğinin değerini almak için bileşenin özelliğini denetleyin <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> .</span><span class="sxs-lookup"><span data-stu-id="b5673-107">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="b5673-108">İletişim kutusunun ağaç görünümünde görünecek en üstteki klasörü ayarlamanız gerekirse, <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> sabit listesinin bir üyesini alan özelliğini ayarlayın <xref:System.Environment.SpecialFolder> .</span><span class="sxs-lookup"><span data-stu-id="b5673-108">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="b5673-109">Ayrıca, <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> klasör tarayıcısı ağaç görünümünün en üstünde görünen metin dizesini belirten özelliğini de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5673-109">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="b5673-110">Aşağıdaki örnekte, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'da bir proje oluştururken olduğu gibi bir klasörü seçmek için kullanılır ve dosyayı kaydetmek için bir klasör seçmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="b5673-110">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="b5673-111">Bu örnekte, klasör adı <xref:System.Windows.Forms.TextBox> form üzerindeki bir denetimde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b5673-111">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="b5673-112">Bu, bir denetim gibi düzenlenebilir bir alana, <xref:System.Windows.Forms.TextBox> kullanıcıların bir hata durumunda veya başka sorunlar durumunda kendi seçimini düzenleyebilmeleri için, konumunu bir şekilde yerleştirmek iyi bir fikir olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5673-112">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="b5673-113">Bu örnekte, bir form ve bir denetim içeren bir form varsayılır <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="b5673-113">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="b5673-114">Bu sınıfı kullanmak için, derlemeniz, numaralandırmanın bir parçası olan özelliği tarafından verilen bir ayrıcalık düzeyi gerektirir <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess> .</span><span class="sxs-lookup"><span data-stu-id="b5673-114">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="b5673-115">Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b5673-115">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="b5673-116">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b5673-116">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="b5673-117">Dosyaları kaydetme hakkında bilgi için bkz. [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="b5673-117">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5673-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5673-118">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="b5673-119">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b5673-119">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="b5673-120">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b5673-120">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
