---
title: "Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d1b4e3fa9b6c6da89abd242be855e9fb7c16dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="264cc-102">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="264cc-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="264cc-103">Aşağıdaki konular, C# ve .NET Framework dosyaları, klasörleri ve kayıt defteri çeşitli temel işlemleri gerçekleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cc-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="264cc-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="264cc-104">In This Section</span></span>  
  
|<span data-ttu-id="264cc-105">**Başlık**</span><span class="sxs-lookup"><span data-stu-id="264cc-105">**Title**</span></span>|<span data-ttu-id="264cc-106">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="264cc-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="264cc-107">Nasıl yapılır: dizin ağacı ile yineleme</span><span class="sxs-lookup"><span data-stu-id="264cc-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="264cc-108">El ile bir dizin ağacı ile yineleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="264cc-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="264cc-109">Nasıl yapılır: dosyalar, klasörler ve sürücüler hakkında bilgi alma</span><span class="sxs-lookup"><span data-stu-id="264cc-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="264cc-110">Oluşturma süreleri ve boyutu gibi dosyalar, klasörler ve sürücüler hakkında bilgi almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cc-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="264cc-111">Nasıl yapılır: bir dosya veya klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="264cc-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="264cc-112">Yeni bir dosya veya klasör oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cc-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="264cc-113">Nasıl yapılır: kopyalama, silme ve taşıma dosyalar ve klasörler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="264cc-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="264cc-114">Kopyalama, silme ve dosya ve klasörleri taşıma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="264cc-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="264cc-115">Nasıl yapılır: dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="264cc-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="264cc-116">Belirli dosya işlemleri için standart bir Windows ilerleme durumu iletişim kutusunu görüntülemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cc-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="264cc-117">Nasıl yapılır: bir metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="264cc-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="264cc-118">Bir metin dosyasına yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="264cc-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="264cc-119">Nasıl yapılır: bir metin dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="264cc-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="264cc-120">Bir metin dosyasından okuma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="264cc-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="264cc-121">Nasıl yapılır: bir metin dosyasını okuma bir satır aynı anda</span><span class="sxs-lookup"><span data-stu-id="264cc-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="264cc-122">Bir defada bir dosya bir satırından metni almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="264cc-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="264cc-123">Nasıl yapılır: kayıt defterinde anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="264cc-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="264cc-124">Sistem kayıt defterine bir anahtar yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="264cc-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="264cc-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="264cc-125">Related Sections</span></span>  
 [<span data-ttu-id="264cc-126">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="264cc-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="264cc-127">Nasıl yapılır: kopyalama, silme ve taşıma dosyalar ve klasörler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="264cc-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="264cc-128">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="264cc-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="264cc-129">Dosyalar, klasörler ve sürücüler</span><span class="sxs-lookup"><span data-stu-id="264cc-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
