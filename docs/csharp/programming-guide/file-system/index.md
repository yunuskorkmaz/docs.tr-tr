---
title: Dosya sistemi ve kayıt defteri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: ef6c1da09ea0435643caba0f5e2819c064f8db01
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589916"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="c2a1c-102">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2a1c-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="c2a1c-103">Aşağıdaki konularda, dosyalar, klasörler ve C# kayıt defteri üzerinde çeşitli temel işlemleri gerçekleştirmek için ve .NET Framework nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2a1c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c2a1c-104">In This Section</span></span>  
  
|<span data-ttu-id="c2a1c-105">**Başlık**</span><span class="sxs-lookup"><span data-stu-id="c2a1c-105">**Title**</span></span>|<span data-ttu-id="c2a1c-106">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c2a1c-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="c2a1c-107">Nasıl yapılır: Dizin ağacı aracılığıyla yineleme</span><span class="sxs-lookup"><span data-stu-id="c2a1c-107">How to: Iterate Through a Directory Tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="c2a1c-108">Bir dizin ağacında el ile nasıl yineleyemezsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="c2a1c-109">Nasıl yapılır: Dosyalar, klasörler ve sürücüler hakkında bilgi alın</span><span class="sxs-lookup"><span data-stu-id="c2a1c-109">How to: Get Information About Files, Folders, and Drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="c2a1c-110">Dosyalar, klasörler ve sürücüler hakkında oluşturma süreleri ve boyutu gibi bilgilerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="c2a1c-111">Nasıl yapılır: Dosya veya klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2a1c-111">How to: Create a File or Folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="c2a1c-112">Yeni bir dosya veya klasör oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="c2a1c-113">Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2a1c-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="c2a1c-114">Dosya ve klasörlerin nasıl kopyalanacağını, silineceğini ve taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="c2a1c-115">Nasıl yapılır: Dosya Işlemleri için Ilerleme durumu Iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="c2a1c-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="c2a1c-116">Belirli dosya işlemleri için standart bir Windows ilerleme durumu iletişim kutusunun nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="c2a1c-117">Nasıl yapılır: Bir metin dosyasına yaz</span><span class="sxs-lookup"><span data-stu-id="c2a1c-117">How to: Write to a Text File</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="c2a1c-118">Bir metin dosyasına nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="c2a1c-119">Nasıl yapılır: Bir metin dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="c2a1c-119">How to: Read From a Text File</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="c2a1c-120">Bir metin dosyasından nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="c2a1c-121">Nasıl yapılır: Bir metin dosyasını tek seferde bir satır okuyun</span><span class="sxs-lookup"><span data-stu-id="c2a1c-121">How to: Read a Text File One Line at a Time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="c2a1c-122">Tek seferde bir dosyadan bir satırdan nasıl metin alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="c2a1c-123">Nasıl yapılır: Kayıt defterinde anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2a1c-123">How to: Create a Key In the Registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="c2a1c-124">Sistem kayıt defterine bir anahtarın nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a1c-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="c2a1c-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c2a1c-125">Related Sections</span></span>  
 [<span data-ttu-id="c2a1c-126">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="c2a1c-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="c2a1c-127">Nasıl yapılır: Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2a1c-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="c2a1c-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2a1c-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="c2a1c-129">Dosyalar, klasörler ve sürücüler</span><span class="sxs-lookup"><span data-stu-id="c2a1c-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
