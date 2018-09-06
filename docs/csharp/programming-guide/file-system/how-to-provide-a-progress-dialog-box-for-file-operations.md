---
title: 'Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: f80bbc94579c58210769800ad8bf74bc60878af5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859979"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="57ff7-102">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="57ff7-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="57ff7-103">Kullanırsanız Windows'da dosya işlemlerinin Windows içinde ilerleme durumunu gösteren standart iletişim kutusunu sağlayabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="57ff7-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="57ff7-104">Visual Studio'da bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="57ff7-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="57ff7-105">Menü çubuğunda, **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="57ff7-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="57ff7-106">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="57ff7-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="57ff7-107">İçinde **derlemeleri** alanında seçin**Framework** tercih değildir.</span><span class="sxs-lookup"><span data-stu-id="57ff7-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="57ff7-108">Adları listesinde seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** iletişim kutusunu kapatmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="57ff7-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ff7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="57ff7-109">Example</span></span>  
 <span data-ttu-id="57ff7-110">Aşağıdaki kodu belirtilen dizine kopyalar, `sourcePath` dizini, `destinationPath` belirtir.</span><span class="sxs-lookup"><span data-stu-id="57ff7-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="57ff7-111">Bu kod Ayrıca işlem tamamlanmadan önce zaman kalan tahmini süreyi gösteren standart iletişim kutusunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="57ff7-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="57ff7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57ff7-112">See Also</span></span>

- [<span data-ttu-id="57ff7-113">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="57ff7-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
