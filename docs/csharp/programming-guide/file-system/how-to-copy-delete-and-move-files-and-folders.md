---
title: Dosyaları ve klasörleri kopyalama, silme ve taşıma-C# Programlama Kılavuzu
description: Dosya, dizin, FileInfo ve DirectoryInfo sınıflarını kullanarak dosya ve klasörleri kopyalama, silme ve taşıma hakkında bilgi edinin.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 24595c9f5c75b70afb0ff079b6b93e35502f7fb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202519"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="acaa8-103">Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="acaa8-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>

<span data-ttu-id="acaa8-104">Aşağıdaki örneklerde, <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> ad alanından,, <xref:System.IO.FileInfo?displayProperty=nameWithType> ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıfları kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir <xref:System.IO?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="acaa8-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="acaa8-105">Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="acaa8-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="acaa8-106">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="acaa8-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="acaa8-107"><xref:System.IO.FileSystemWatcher?displayProperty=nameWithType>Birden çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="acaa8-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="acaa8-108">Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="acaa8-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="acaa8-109">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="acaa8-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acaa8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="acaa8-110">Example</span></span>  

 <span data-ttu-id="acaa8-111">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="acaa8-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="acaa8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="acaa8-112">Example</span></span>  

 <span data-ttu-id="acaa8-113">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="acaa8-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="acaa8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="acaa8-114">Example</span></span>  

 <span data-ttu-id="acaa8-115">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="acaa8-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="acaa8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acaa8-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="acaa8-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="acaa8-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="acaa8-118">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="acaa8-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="acaa8-119">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="acaa8-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="acaa8-120">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="acaa8-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="acaa8-121">Ortak g/ç görevleri</span><span class="sxs-lookup"><span data-stu-id="acaa8-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
