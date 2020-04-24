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
ms.openlocfilehash: 22bcd0f1f3acb0c0ad899b83ad2d879ead948f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348905"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="996b0-102">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="996b0-102">File Access with Visual Basic</span></span>

<span data-ttu-id="996b0-103">`My.Computer.FileSystem` Nesnesi dosya ve klasörlerle çalışmaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="996b0-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="996b0-104">Özellikleri, yöntemleri ve olayları, dosya ve klasör oluşturmanızı, kopyalamanızı, taşımanızı, araştırmanızı ve silmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="996b0-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="996b0-105">`My.Computer.FileSystem`, geriye dönük uyumluluk için Visual Basic tarafından sağlanan`FileOpen`eski `FileClose`işlevlerden `Input`( `InputString`, `LineInput`,,, vb.) daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="996b0-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="996b0-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="996b0-106">In This Section</span></span>  

 [<span data-ttu-id="996b0-107">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="996b0-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="996b0-108">Dosyalardan okumak için `My.Computer.FileSystem` nesnesini kullanma ile ilgili konuları listeler</span><span class="sxs-lookup"><span data-stu-id="996b0-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="996b0-109">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="996b0-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="996b0-110">Dosyalara yazmak için `My.Computer.FileSystem` nesnesini kullanma ile ilgili konuları listeler</span><span class="sxs-lookup"><span data-stu-id="996b0-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="996b0-111">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="996b0-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="996b0-112">Dosya ve klasörleri oluşturmak, kopyalamak `My.Computer.FileSystem` , silmek ve taşımak için nesnesini kullanma ile ilgili konuları listeler.</span><span class="sxs-lookup"><span data-stu-id="996b0-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="996b0-113">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="996b0-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="996b0-114">' Nin, `TextFieldReader` Günlükler gibi metin dosyalarını ayrıştırmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="996b0-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="996b0-115">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="996b0-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="996b0-116">Dosya kodlamalarını ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="996b0-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="996b0-117">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="996b0-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="996b0-118">Dosyalar ve klasörler hakkında bilgi raporlayan bir yardımcı programın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="996b0-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="996b0-119">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="996b0-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="996b0-120">Metin dosyalarını okurken ve yazarken karşılaşılan yaygın sorunları listeler ve her biri için düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="996b0-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
