---
title: "Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac68b5aa6014db87b4f7a269ef73d0608371bd8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="11893-102">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="11893-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="11893-103">Kullanıyorsanız Windows dosya işlemlerini ilerleme durumunu gösteren bir standart iletişim kutusu sağlayabilir <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yönteminde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="11893-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="11893-104">Visual Studio'da bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="11893-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="11893-105">Menü çubuğunda seçin **proje**, **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="11893-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="11893-106">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="11893-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="11893-107">İçinde **derlemeleri** alanı seçin**Framework** tercih değil.</span><span class="sxs-lookup"><span data-stu-id="11893-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="11893-108">Adları listesinden seçin **Microsoft.VisualBasic** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="11893-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11893-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="11893-109">Example</span></span>  
 <span data-ttu-id="11893-110">Aşağıdaki kod dizine kopyalar, `sourcePath` dizine belirtir, `destinationPath` belirtir.</span><span class="sxs-lookup"><span data-stu-id="11893-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="11893-111">Bu kod ayrıca işlemi tamamlanmadan önce kalan süre tahmini miktarını gösteren bir standart iletişim kutusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="11893-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="11893-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11893-112">See Also</span></span>  
 [<span data-ttu-id="11893-113">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="11893-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
