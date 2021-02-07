---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic dosya erişimi'
title: Dosya erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: b3ea742185e7219ce7fdfb8eee987fd9c17e3a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666322"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="26eb4-103">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="26eb4-103">File Access with Visual Basic</span></span>

<span data-ttu-id="26eb4-104">`My.Computer.FileSystem`Nesnesi dosya ve klasörlerle çalışmaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="26eb4-104">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="26eb4-105">Özellikleri, yöntemleri ve olayları, dosya ve klasör oluşturmanızı, kopyalamanızı, taşımanızı, araştırmanızı ve silmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26eb4-105">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="26eb4-106">`My.Computer.FileSystem``FileOpen`, `FileClose` `Input` `InputString` `LineInput` geriye dönük uyumluluk için Visual Basic tarafından sağlanan eski işlevlerden (,,,, vb.) daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="26eb4-106">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26eb4-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="26eb4-107">In This Section</span></span>  

 [<span data-ttu-id="26eb4-108">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="26eb4-108">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="26eb4-109">Dosyalardan okumak için nesnesini kullanma ile ilgili konuları listeler `My.Computer.FileSystem`</span><span class="sxs-lookup"><span data-stu-id="26eb4-109">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="26eb4-110">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="26eb4-110">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="26eb4-111">Dosyalara yazmak için nesnesini kullanma ile ilgili konuları listeler `My.Computer.FileSystem`</span><span class="sxs-lookup"><span data-stu-id="26eb4-111">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="26eb4-112">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="26eb4-112">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="26eb4-113">`My.Computer.FileSystem`Dosya ve klasörleri oluşturmak, kopyalamak, silmek ve taşımak için nesnesini kullanma ile ilgili konuları listeler.</span><span class="sxs-lookup"><span data-stu-id="26eb4-113">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="26eb4-114">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="26eb4-114">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="26eb4-115">' Nin, Günlükler gibi `TextFieldReader` metin dosyalarını ayrıştırmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="26eb4-115">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="26eb4-116">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="26eb4-116">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="26eb4-117">Dosya kodlamalarını ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="26eb4-117">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="26eb4-118">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="26eb4-118">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="26eb4-119">Dosyalar ve klasörler hakkında bilgi raporlayan bir yardımcı programın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26eb4-119">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="26eb4-120">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="26eb4-120">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="26eb4-121">Metin dosyalarını okurken ve yazarken karşılaşılan yaygın sorunları listeler ve her biri için düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="26eb4-121">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
