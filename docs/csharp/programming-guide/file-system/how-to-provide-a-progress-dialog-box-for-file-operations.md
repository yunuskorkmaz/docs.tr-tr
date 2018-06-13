---
title: 'Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331168"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="0907e-102">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0907e-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="0907e-103">Kullanıyorsanız Windows dosya işlemlerini ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilir <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0907e-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="0907e-104">Visual Studio'da bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="0907e-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="0907e-105">Menü çubuğunda seçin **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="0907e-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="0907e-106">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0907e-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="0907e-107">İçinde **derlemeleri** alanı seçin**Framework** tercih değil.</span><span class="sxs-lookup"><span data-stu-id="0907e-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="0907e-108">Adları listesinden seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="0907e-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0907e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0907e-109">Example</span></span>  
 <span data-ttu-id="0907e-110">Aşağıdaki kod dizine kopyalar, `sourcePath` dizine belirtir, `destinationPath` belirtir.</span><span class="sxs-lookup"><span data-stu-id="0907e-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="0907e-111">Bu kod ayrıca işlemi tamamlanmadan önce kalan süre tahmini miktarını gösteren bir standart iletişim kutusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="0907e-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0907e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0907e-112">See Also</span></span>  
 [<span data-ttu-id="0907e-113">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0907e-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
