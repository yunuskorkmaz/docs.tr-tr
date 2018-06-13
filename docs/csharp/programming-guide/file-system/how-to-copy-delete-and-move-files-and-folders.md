---
title: 'Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 5debb2cbfa5ada45447e280169b9fe66d1a15a53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330086"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="34d47-102">Nasıl yapılır: Dosyaları ve Klasörleri Kopyalama, Silme ve Taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="34d47-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="34d47-103">Aşağıdaki örnekler nasıl kopyalama, taşıma ve dosya ve klasörlerin zaman uyumlu bir biçimde kullanarak silme <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, ve <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> gelen sınıfları <xref:System.IO?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="34d47-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="34d47-104">Bu örnekler, bir ilerleme çubuğu veya herhangi bir kullanıcı arabirimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="34d47-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="34d47-105">Standart ilerleme durumu iletişim kutusu sağlamak istiyorsanız, bkz: [nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="34d47-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="34d47-106">Kullanım <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> , birden çok dosya çalışırken ilerleme durumunu hesaplamak sağlayacaktır olaylarını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="34d47-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="34d47-107">Başka bir yaklaşım platform kullanmaktır Windows Kabuğu'nda ilgili dosya ile ilgili yöntemleri çağırmak için çağırma.</span><span class="sxs-lookup"><span data-stu-id="34d47-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="34d47-108">Bu dosya işlemlerini zaman uyumsuz olarak gerçekleştirme hakkında daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="34d47-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d47-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="34d47-109">Example</span></span>  
 <span data-ttu-id="34d47-110">Aşağıdaki örnekte, dosyaları ve dizinleri kopyalamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="34d47-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="34d47-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="34d47-111">Example</span></span>  
 <span data-ttu-id="34d47-112">Aşağıdaki örnekte, dosyaları ve dizinleri taşımak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="34d47-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="34d47-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="34d47-113">Example</span></span>  
 <span data-ttu-id="34d47-114">Aşağıdaki örnek, dosya ve dizinleri silme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="34d47-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="34d47-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34d47-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="34d47-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="34d47-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="34d47-117">Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="34d47-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="34d47-118">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama</span><span class="sxs-lookup"><span data-stu-id="34d47-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="34d47-119">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="34d47-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="34d47-120">Ortak G/Ç Görevleri</span><span class="sxs-lookup"><span data-stu-id="34d47-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
