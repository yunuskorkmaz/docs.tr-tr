---
title: 'Nasıl Yapılır: Dosya işlemleri için - ilerleme durumu iletişim kutusu sağlar C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 13f924566df0d7fe601e32bfe74878c18d8e64b8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245395"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="6b6a5-102">Nasıl Yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6b6a5-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="6b6a5-103">Kullanırsanız Windows'da dosya işlemlerinin Windows içinde ilerleme durumunu gösteren standart iletişim kutusunu sağlayabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="6b6a5-104">Visual Studio'da bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="6b6a5-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="6b6a5-105">Menü çubuğunda, **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="6b6a5-106">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="6b6a5-107">İçinde **derlemeleri** alanında seçin **Framework** tercih değildir.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="6b6a5-108">Adları listesinde seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** iletişim kutusunu kapatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b6a5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b6a5-109">Example</span></span>  
 <span data-ttu-id="6b6a5-110">Aşağıdaki kodu belirtilen dizine kopyalar, `sourcePath` dizini, `destinationPath` belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="6b6a5-111">Bu kod Ayrıca işlem tamamlanmadan önce zaman kalan tahmini süreyi gösteren standart iletişim kutusunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6b6a5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b6a5-112">See Also</span></span>

- [<span data-ttu-id="6b6a5-113">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6b6a5-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
