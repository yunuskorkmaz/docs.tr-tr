---
title: Dosya işlemleri için ilerleme iletişim kutusu nasıl sağlanabilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705138"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="0f482-102">Dosya işlemleri için ilerleme iletişim kutusu nasıl sağlanabilir (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f482-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="0f482-103">Ad alanında <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> yöntemi <xref:Microsoft.VisualBasic?displayProperty=nameWithType> kullanıyorsanız, Windows'daki dosya işlemlerinde ilerlemeyi gösteren standart bir iletişim kutusu sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f482-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="0f482-104">Visual Studio'da referans eklemek için</span><span class="sxs-lookup"><span data-stu-id="0f482-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="0f482-105">Menü çubuğunda **Proje**, **Başvuru Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="0f482-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="0f482-106">**Başvuru Yöneticisi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f482-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="0f482-107">**Derlemeler** alanında, önceden seçilmemişse **Çerçeve'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="0f482-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="0f482-108">Adlar listesinde **Microsoft.VisualBasic** onay kutusunu seçin ve ardından iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0f482-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f482-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f482-109">Example</span></span>  
 <span data-ttu-id="0f482-110">Aşağıdaki kod, `sourcePath` `destinationPath` belirten dizine belirten dizin kopyaları.</span><span class="sxs-lookup"><span data-stu-id="0f482-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="0f482-111">Bu kod, işlem bitmeden önce kalan tahmini süreyi gösteren standart bir iletişim kutusu da sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f482-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="0f482-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f482-112">See also</span></span>

- [<span data-ttu-id="0f482-113">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f482-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
