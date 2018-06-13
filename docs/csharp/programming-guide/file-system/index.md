---
title: Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 20e8b857759253736d11bc31988fadb4843fa87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334866"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="0aa56-102">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0aa56-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="0aa56-103">Aşağıdaki konular, C# ve .NET Framework dosyaları, klasörleri ve kayıt defteri çeşitli temel işlemleri gerçekleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0aa56-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0aa56-104">In This Section</span></span>  
  
|<span data-ttu-id="0aa56-105">**Başlık**</span><span class="sxs-lookup"><span data-stu-id="0aa56-105">**Title**</span></span>|<span data-ttu-id="0aa56-106">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0aa56-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="0aa56-107">Nasıl yapılır: Dizin Ağacı ile Yineleme</span><span class="sxs-lookup"><span data-stu-id="0aa56-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="0aa56-108">El ile bir dizin ağacı ile yineleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="0aa56-109">Nasıl yapılır: dosyalar, klasörler ve sürücüler hakkında bilgi alma</span><span class="sxs-lookup"><span data-stu-id="0aa56-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="0aa56-110">Oluşturma süreleri ve boyutu gibi dosyalar, klasörler ve sürücüler hakkında bilgi almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="0aa56-111">Nasıl yapılır: Dosya veya Klasör Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0aa56-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="0aa56-112">Yeni bir dosya veya klasör oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="0aa56-113">Nasıl yapılır: kopyalama, silme ve taşıma dosyalar ve klasörler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0aa56-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="0aa56-114">Kopyalama, silme ve dosya ve klasörleri taşıma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="0aa56-115">Nasıl yapılır: Dosya İşlemleri için İlerleme Durumu İletişim Kutusu Sağlama</span><span class="sxs-lookup"><span data-stu-id="0aa56-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="0aa56-116">Belirli dosya işlemleri için standart bir Windows ilerleme durumu iletişim kutusunu görüntülemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="0aa56-117">Nasıl yapılır: Bir Metin Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="0aa56-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="0aa56-118">Bir metin dosyasına yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="0aa56-119">Nasıl yapılır: Metin Dosyasından Okuma</span><span class="sxs-lookup"><span data-stu-id="0aa56-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="0aa56-120">Bir metin dosyasından okuma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="0aa56-121">Nasıl yapılır: bir metin dosyasını okuma bir satır aynı anda</span><span class="sxs-lookup"><span data-stu-id="0aa56-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="0aa56-122">Bir defada bir dosya bir satırından metni almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="0aa56-123">Nasıl yapılır: kayıt defterinde anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="0aa56-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="0aa56-124">Sistem kayıt defterine bir anahtar yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0aa56-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="0aa56-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0aa56-125">Related Sections</span></span>  
 [<span data-ttu-id="0aa56-126">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="0aa56-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="0aa56-127">Nasıl yapılır: kopyalama, silme ve taşıma dosyalar ve klasörler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0aa56-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="0aa56-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0aa56-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="0aa56-129">Dosyalar, klasörler ve sürücüler</span><span class="sxs-lookup"><span data-stu-id="0aa56-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
