---
title: "Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="05517-102">Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="05517-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="05517-103">Aşağıdaki örnekler nasıl kopyalama, taşıma ve dosya ve klasörlerin zaman uyumlu bir biçimde kullanarak silme <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıfları <xref:System.IO?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="05517-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="05517-104">Bu örnekler, bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="05517-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="05517-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz: [nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="05517-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="05517-106">Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesaplamak sağlayacaktır olaylarını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="05517-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="05517-107">Başka bir yaklaşım platform kullanmaktır Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağırma.</span><span class="sxs-lookup"><span data-stu-id="05517-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="05517-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="05517-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05517-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="05517-109">Example</span></span>  
 <span data-ttu-id="05517-110">Aşağıdaki örnekte, dosyaları ve dizinleri kopyalamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05517-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="05517-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="05517-111">Example</span></span>  
 <span data-ttu-id="05517-112">Aşağıdaki örnekte, dosyaları ve dizinleri taşımak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05517-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="05517-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="05517-113">Example</span></span>  
 <span data-ttu-id="05517-114">Aşağıdaki örnek, dosya ve dizinleri silme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05517-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="05517-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05517-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="05517-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="05517-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="05517-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="05517-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="05517-118">Nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="05517-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="05517-119">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="05517-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="05517-120">Ortak g/ç görevleri</span><span class="sxs-lookup"><span data-stu-id="05517-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
