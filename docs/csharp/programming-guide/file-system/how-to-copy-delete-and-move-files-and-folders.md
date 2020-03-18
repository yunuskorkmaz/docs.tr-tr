---
title: Dosya ve klasörleri kopyalama, silme ve taşıma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712279"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="929d9-102">Dosya ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="929d9-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="929d9-103">Aşağıdaki örnekler, <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> <xref:System.IO?displayProperty=nameWithType> ad alanından , , ve sınıfları kullanarak dosya ve klasörleri eşzamanlı bir şekilde kopyalama, taşıma ve silme yi gösterir.</span><span class="sxs-lookup"><span data-stu-id="929d9-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="929d9-104">Bu örnekler bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="929d9-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="929d9-105">Standart bir ilerleme iletişim kutusu sağlamak istiyorsanız, [dosya işlemleri için ilerleme iletişim kutusunun nasıl sağlayabileceğinize](how-to-provide-a-progress-dialog-box-for-file-operations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="929d9-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="929d9-106">Birden <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> çok dosya üzerinde çalışırken ilerlemeyi hesaplamanızı sağlayacak olayları sağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="929d9-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="929d9-107">Diğer bir yaklaşım, Windows Shell'deki ilgili dosya yla ilgili yöntemleri çağırmak için platform çağrısı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="929d9-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="929d9-108">Bu dosya işlemlerinin eş senkronize olarak nasıl gerçekleştirilecek hakkında bilgi [için, Bkz.](../../../standard/io/asynchronous-file-i-o.md)</span><span class="sxs-lookup"><span data-stu-id="929d9-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="929d9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="929d9-109">Example</span></span>  
 <span data-ttu-id="929d9-110">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanılsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="929d9-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="929d9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="929d9-111">Example</span></span>  
 <span data-ttu-id="929d9-112">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="929d9-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="929d9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="929d9-113">Example</span></span>  
 <span data-ttu-id="929d9-114">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="929d9-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="929d9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="929d9-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="929d9-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="929d9-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="929d9-117">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="929d9-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="929d9-118">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="929d9-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="929d9-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="929d9-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="929d9-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="929d9-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
