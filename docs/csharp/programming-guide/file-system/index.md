---
title: Dosya sistemi ve kayıt defteri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: f160df456f1a3437e11de2d3660d158ae4d4bb67
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900572"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="2482e-102">Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2482e-102">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="2482e-103">Aşağıdaki makalelerde dosyalar, klasörler ve kayıt C# defteri üzerinde çeşitli temel işlemleri gerçekleştirmek için ve .NET kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2482e-103">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2482e-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="2482e-104">In this section</span></span>

|<span data-ttu-id="2482e-105">**Başlık**</span><span class="sxs-lookup"><span data-stu-id="2482e-105">**Title**</span></span>|<span data-ttu-id="2482e-106">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2482e-106">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="2482e-107">Bir dizin ağacında yineleme yapma</span><span class="sxs-lookup"><span data-stu-id="2482e-107">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="2482e-108">Bir dizin ağacında el ile nasıl yineleyemezsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-108">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="2482e-109">Dosyalar, klasörler ve sürücüler hakkında bilgi alma</span><span class="sxs-lookup"><span data-stu-id="2482e-109">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="2482e-110">Dosyalar, klasörler ve sürücüler hakkında oluşturma süreleri ve boyutu gibi bilgilerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="2482e-111">Dosya veya klasör oluşturma</span><span class="sxs-lookup"><span data-stu-id="2482e-111">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="2482e-112">Yeni bir dosya veya klasör oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-112">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="2482e-113">Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2482e-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="2482e-114">Dosya ve klasörlerin nasıl kopyalanacağını, silineceğini ve taşınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-114">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="2482e-115">Dosya işlemleri için ilerleme durumu iletişim kutusu sağlama</span><span class="sxs-lookup"><span data-stu-id="2482e-115">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="2482e-116">Belirli dosya işlemleri için standart bir Windows ilerleme durumu iletişim kutusunun nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="2482e-117">Metin dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="2482e-117">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="2482e-118">Bir metin dosyasına nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-118">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="2482e-119">Bir metin dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="2482e-119">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="2482e-120">Bir metin dosyasından nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-120">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="2482e-121">Bir metin dosyasını tek seferde bir satır okuma</span><span class="sxs-lookup"><span data-stu-id="2482e-121">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="2482e-122">Tek seferde bir dosyadan bir satırdan nasıl metin alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-122">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="2482e-123">Kayıt defterinde anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="2482e-123">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="2482e-124">Sistem kayıt defterine bir anahtarın nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2482e-124">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="2482e-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="2482e-125">Related sections</span></span>

- [<span data-ttu-id="2482e-126">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="2482e-126">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="2482e-127">Dosyaları ve klasörleri kopyalama, silme ve taşıma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2482e-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="2482e-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2482e-128">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
