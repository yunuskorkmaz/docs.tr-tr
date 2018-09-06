---
title: 'Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: a9c5b1dc35878ac2e50a7c4ec72251885704fea6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858349"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="8a150-102">Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8a150-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="8a150-103">Aşağıdaki örnekler kopyalayın, taşıma ve dosya ve klasörleri kullanarak zaman uyumlu bir şekilde silmek nasıl <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıflar <xref:System.IO?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8a150-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8a150-104">Bu örneklerde bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8a150-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="8a150-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz. [nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8a150-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="8a150-106">Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesapla olanak tanıyacak olayları sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="8a150-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="8a150-107">Başka bir yaklaşım platform kullanmaktır. Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağır.</span><span class="sxs-lookup"><span data-stu-id="8a150-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="8a150-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="8a150-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a150-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a150-109">Example</span></span>  
 <span data-ttu-id="8a150-110">Aşağıdaki örnek, dosya ve dizinleri kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a150-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8a150-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a150-111">Example</span></span>  
 <span data-ttu-id="8a150-112">Aşağıdaki örnek, dosya ve dizinleri taşıma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a150-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8a150-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a150-113">Example</span></span>  
 <span data-ttu-id="8a150-114">Aşağıdaki örnek, dosyaları ve dizinleri silme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a150-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8a150-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a150-115">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="8a150-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8a150-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8a150-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8a150-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
- [<span data-ttu-id="8a150-118">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama</span><span class="sxs-lookup"><span data-stu-id="8a150-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [<span data-ttu-id="8a150-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="8a150-119">File and Stream I/O</span></span>](../../../standard/io/index.md)  
- [<span data-ttu-id="8a150-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="8a150-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
