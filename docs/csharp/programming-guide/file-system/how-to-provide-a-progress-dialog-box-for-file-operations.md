---
title: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama-C# Programlama Kılavuzu
description: Dosya işlemleri için CopyFile (dize, dize, UIOption) yöntemi kullanılarak bir ilerleme durumu iletişim kutusu sağlamayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 5d16aeb3a5394ca250e4a5e26074db797c54216d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185892"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="746f7-103">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="746f7-103">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>

<span data-ttu-id="746f7-104">Ad alanında yöntemini kullanırsanız, Windows 'daki dosya işlemlerinde ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> <xref:Microsoft.VisualBasic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="746f7-104">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="746f7-105">Visual Studio 'da bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="746f7-105">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="746f7-106">Menü çubuğunda **Proje**, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="746f7-106">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="746f7-107">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="746f7-107">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="746f7-108">**Derlemeler** alanında, zaten seçili değilse **Framework** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="746f7-108">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="746f7-109">Ad listesinde, **Microsoft. VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="746f7-109">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="746f7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="746f7-110">Example</span></span>  

 <span data-ttu-id="746f7-111">Aşağıdaki kod, belirten dizinini belirten `sourcePath` dizine kopyalar `destinationPath` .</span><span class="sxs-lookup"><span data-stu-id="746f7-111">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="746f7-112">Bu kod ayrıca, işlem tamamlanmadan önce kalan tahmini süreyi gösteren standart bir iletişim kutusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="746f7-112">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="746f7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="746f7-113">See also</span></span>

- [<span data-ttu-id="746f7-114">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="746f7-114">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
