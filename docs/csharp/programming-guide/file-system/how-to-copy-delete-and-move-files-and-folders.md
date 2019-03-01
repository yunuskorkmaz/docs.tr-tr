---
title: 'Nasıl yapılır: Kopyalama, silme, taşıma dosya ve klasörleri - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 609e14141538543c9318efbd4899ec16967cc23f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972080"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="49bc8-102">Nasıl yapılır: Kopyalama, silme ve taşıma dosya ve klasörleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="49bc8-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="49bc8-103">Aşağıdaki örnekler kopyalayın, taşıma ve dosya ve klasörleri kullanarak zaman uyumlu bir şekilde silmek nasıl <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıflar <xref:System.IO?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="49bc8-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="49bc8-104">Bu örneklerde bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="49bc8-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="49bc8-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [nasıl yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="49bc8-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="49bc8-106">Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesapla olanak tanıyacak olayları sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="49bc8-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="49bc8-107">Başka bir yaklaşım platform kullanmaktır. Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağır.</span><span class="sxs-lookup"><span data-stu-id="49bc8-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="49bc8-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="49bc8-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49bc8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="49bc8-109">Example</span></span>  
 <span data-ttu-id="49bc8-110">Aşağıdaki örnek, dosya ve dizinleri kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49bc8-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="49bc8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="49bc8-111">Example</span></span>  
 <span data-ttu-id="49bc8-112">Aşağıdaki örnek, dosya ve dizinleri taşıma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49bc8-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="49bc8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="49bc8-113">Example</span></span>  
 <span data-ttu-id="49bc8-114">Aşağıdaki örnek, dosyaları ve dizinleri silme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="49bc8-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="49bc8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49bc8-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="49bc8-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="49bc8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="49bc8-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="49bc8-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="49bc8-118">Nasıl yapılır: Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="49bc8-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="49bc8-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="49bc8-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="49bc8-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="49bc8-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
