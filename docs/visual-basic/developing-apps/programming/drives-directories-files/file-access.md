---
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
ms.openlocfilehash: 3b2042862ae81a52d62374e35a456766ed47edc9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401738"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="a2232-102">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="a2232-102">File Access with Visual Basic</span></span>

<span data-ttu-id="a2232-103">`My.Computer.FileSystem`Nesnesi dosya ve klasörlerle çalışmaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2232-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="a2232-104">Özellikleri, yöntemleri ve olayları, dosya ve klasör oluşturmanızı, kopyalamanızı, taşımanızı, araştırmanızı ve silmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2232-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="a2232-105">`My.Computer.FileSystem``FileOpen`, `FileClose` `Input` `InputString` `LineInput` geriye dönük uyumluluk için Visual Basic tarafından sağlanan eski işlevlerden (,,,, vb.) daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2232-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2232-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2232-106">In This Section</span></span>  

 [<span data-ttu-id="a2232-107">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="a2232-107">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="a2232-108">Dosyalardan okumak için nesnesini kullanma ile ilgili konuları listeler `My.Computer.FileSystem`</span><span class="sxs-lookup"><span data-stu-id="a2232-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="a2232-109">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="a2232-109">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="a2232-110">Dosyalara yazmak için nesnesini kullanma ile ilgili konuları listeler `My.Computer.FileSystem`</span><span class="sxs-lookup"><span data-stu-id="a2232-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="a2232-111">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="a2232-111">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="a2232-112">`My.Computer.FileSystem`Dosya ve klasörleri oluşturmak, kopyalamak, silmek ve taşımak için nesnesini kullanma ile ilgili konuları listeler.</span><span class="sxs-lookup"><span data-stu-id="a2232-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="a2232-113">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a2232-113">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="a2232-114">' Nin, Günlükler gibi `TextFieldReader` metin dosyalarını ayrıştırmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2232-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="a2232-115">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="a2232-115">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="a2232-116">Dosya kodlamalarını ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2232-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="a2232-117">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a2232-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="a2232-118">Dosyalar ve klasörler hakkında bilgi raporlayan bir yardımcı programın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2232-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="a2232-119">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="a2232-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="a2232-120">Metin dosyalarını okurken ve yazarken karşılaşılan yaygın sorunları listeler ve her biri için düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="a2232-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
