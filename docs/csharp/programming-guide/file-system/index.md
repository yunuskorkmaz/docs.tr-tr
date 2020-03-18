---
title: Dosya sistemi ve kayıt defteri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900572"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="da8ca-102">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da8ca-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="da8ca-103">Aşağıdaki makaleler, dosyalar, klasörler ve kayıt defteri üzerinde çeşitli temel işlemleri gerçekleştirmek için C# ve .NET'in nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="da8ca-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="da8ca-104">In this section</span></span>

|<span data-ttu-id="da8ca-105">**Başlık**</span><span class="sxs-lookup"><span data-stu-id="da8ca-105">**Title**</span></span>|<span data-ttu-id="da8ca-106">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="da8ca-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="da8ca-107">Dizin ağacında yineleme</span><span class="sxs-lookup"><span data-stu-id="da8ca-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="da8ca-108">Dizin ağacında el ile nasıl yinelenin izini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="da8ca-109">Dosyalar, klasörler ve sürücüler hakkında bilgi alma</span><span class="sxs-lookup"><span data-stu-id="da8ca-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="da8ca-110">Oluşturma süreleri ve boyutu, dosyalar, klasörler ve sürücüler hakkında nasıl bilgi alınır gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="da8ca-111">Dosya veya klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="da8ca-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="da8ca-112">Yeni bir dosya veya klasörün nasıl oluşturultur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="da8ca-113">Dosya ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da8ca-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="da8ca-114">Dosya ve klasörlerin nasıl kopyalanın, silinip taşınır, silinir ve taşınacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="da8ca-115">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="da8ca-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="da8ca-116">Belirli dosya işlemleri için standart bir Windows ilerleme iletişim kutusunun nasıl görüntülenebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="da8ca-117">Bir metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="da8ca-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="da8ca-118">Metin dosyasına nasıl yazılsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="da8ca-119">Metin dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="da8ca-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="da8ca-120">Metin dosyasından nasıl okunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="da8ca-121">Her seferinde tek satır olmak üzere bir metin dosyasını okuma</span><span class="sxs-lookup"><span data-stu-id="da8ca-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="da8ca-122">Bir dosyadan tek satırlık metin alma nın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="da8ca-123">Kayıt defterinde anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="da8ca-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="da8ca-124">Sistem kayıt defterine nasıl bir anahtar yazılsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="da8ca-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="da8ca-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="da8ca-125">Related sections</span></span>

- [<span data-ttu-id="da8ca-126">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="da8ca-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="da8ca-127">Dosya ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da8ca-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="da8ca-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da8ca-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
