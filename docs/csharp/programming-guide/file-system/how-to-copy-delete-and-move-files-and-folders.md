---
title: Dosyaları ve klasörleri kopyalama, silme ve taşıma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712279"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="43fda-102">Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="43fda-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="43fda-103">Aşağıdaki örneklerde, <xref:System.IO?displayProperty=nameWithType> ad alanındaki <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıflarını kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="43fda-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="43fda-104">Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="43fda-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="43fda-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="43fda-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="43fda-106">Birden çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="43fda-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="43fda-107">Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="43fda-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="43fda-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="43fda-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43fda-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="43fda-109">Example</span></span>  
 <span data-ttu-id="43fda-110">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43fda-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="43fda-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="43fda-111">Example</span></span>  
 <span data-ttu-id="43fda-112">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43fda-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="43fda-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="43fda-113">Example</span></span>  
 <span data-ttu-id="43fda-114">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="43fda-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="43fda-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43fda-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="43fda-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="43fda-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="43fda-117">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="43fda-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="43fda-118">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="43fda-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="43fda-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="43fda-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="43fda-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="43fda-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
