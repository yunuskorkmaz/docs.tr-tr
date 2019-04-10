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
ms.openlocfilehash: 050af6d10faec3dd09998349dcf96e96ea0f9201
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306195"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="9ea78-102">Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme</span><span class="sxs-lookup"><span data-stu-id="9ea78-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="9ea78-103">Genellikle, Windows, içinde oluşturduğunuz uygulamalar, en sık dosya kümesini kaydetmek için bir klasör seçmek için kullanıcılara sor gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="9ea78-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="9ea78-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşen kolayca bu görevi gerçekleştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ea78-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="9ea78-105">FolderBrowserDialog bileşeni ile klasörleri seçme</span><span class="sxs-lookup"><span data-stu-id="9ea78-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1. <span data-ttu-id="9ea78-106">Bir yordamda denetleyin <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.Form.DialogResult%2A> iletişim kutusu nasıl kapatıldığı görmek ve değerini almak için özellik <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9ea78-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2. <span data-ttu-id="9ea78-107">İletişim kutusunun ağacı görünümü içinde görünecek kümesi en üstteki klasöre ihtiyacınız varsa, ayarlayın <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> üyesi özelliği <xref:System.Environment.SpecialFolder> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="9ea78-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3. <span data-ttu-id="9ea78-108">Ayrıca, ayarlayabileceğiniz <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> metin dizesini belirtir. özellik, klasör tarayıcı ağaç görünümü üst kısmında görünür.</span><span class="sxs-lookup"><span data-stu-id="9ea78-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="9ea78-109">Aşağıdaki örnekte <xref:System.Windows.Forms.FolderBrowserDialog> bileşen ne zaman Visual Studio'da bir proje oluşturun ve içine kaydetmek için bir klasör seçmeniz istenir benzer bir klasör seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ea78-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="9ea78-110">Bu örnekte, klasör adı ardından görüntülenen bir <xref:System.Windows.Forms.TextBox> form denetimi.</span><span class="sxs-lookup"><span data-stu-id="9ea78-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="9ea78-111">Konumun düzenlenebilir bir alanda gibi yerleştirmek için iyi bir fikirdir bir <xref:System.Windows.Forms.TextBox> denetlemek ve böylece kullanıcılar kendi seçimi hata veya diğer sorunları durumunda düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ea78-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="9ea78-112">Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni ve bir <xref:System.Windows.Forms.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9ea78-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
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
    >  <span data-ttu-id="9ea78-113">Bu sınıf kullanmak için ayrıcalık düzeyi verilen tarafından derlemeyi <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> parçası olan özelliği, <xref:System.Security.Permissions.FileIOPermissionAccess> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="9ea78-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="9ea78-114">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle özel bir durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="9ea78-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="9ea78-115">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="9ea78-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="9ea78-116">Dosyaları kaydetme hakkında daha fazla bilgi için bkz: [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="9ea78-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea78-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ea78-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="9ea78-118">FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9ea78-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="9ea78-119">FolderBrowserDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="9ea78-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
