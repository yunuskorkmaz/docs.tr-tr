---
title: 'Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590092"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="e90d6-102">Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e90d6-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="e90d6-103">Aşağıdaki <xref:System.IO.File?displayProperty=nameWithType>örneklerde, ad<xref:System.IO?displayProperty=nameWithType> alanından <xref:System.IO.FileInfo?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> sınıfları kullanarak dosya ve klasörleri zaman uyumlu bir şekilde kopyalama, taşıma ve silme işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e90d6-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e90d6-104">Bu örnekler, bir ilerleme çubuğu veya başka bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e90d6-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="e90d6-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz [. nasıl yapılır: Dosya Işlemleri](how-to-provide-a-progress-dialog-box-for-file-operations.md)Için bir Ilerleme durumu iletişim kutusu belirtin.</span><span class="sxs-lookup"><span data-stu-id="e90d6-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="e90d6-106">Birden <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> çok dosya üzerinde çalışırken ilerlemeyi hesaplamanıza olanak sağlayacak olayları sağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e90d6-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="e90d6-107">Diğer bir yaklaşım, Windows kabuğu 'nda dosyayla ilgili ilgili yöntemleri çağırmak için platform çağırma kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e90d6-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="e90d6-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="e90d6-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e90d6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e90d6-109">Example</span></span>  
 <span data-ttu-id="e90d6-110">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl kopyalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e90d6-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="e90d6-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e90d6-111">Example</span></span>  
 <span data-ttu-id="e90d6-112">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e90d6-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="e90d6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e90d6-113">Example</span></span>  
 <span data-ttu-id="e90d6-114">Aşağıdaki örnek, dosyaların ve dizinlerin nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e90d6-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e90d6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e90d6-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="e90d6-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e90d6-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e90d6-117">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e90d6-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="e90d6-118">Nasıl yapılır: Dosya Işlemleri için Ilerleme durumu Iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="e90d6-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="e90d6-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="e90d6-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="e90d6-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="e90d6-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
