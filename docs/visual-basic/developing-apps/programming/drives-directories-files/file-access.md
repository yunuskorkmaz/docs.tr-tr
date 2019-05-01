---
title: Visual Basic ile Dosya Erişimi
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
ms.openlocfilehash: f9cbb255dea8c6915951b5099f40bfd0ba66c8aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960309"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="cac5a-102">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="cac5a-102">File Access with Visual Basic</span></span>
<span data-ttu-id="cac5a-103">`My.Computer.FileSystem` Nesne dosyaları ve klasörleri ile çalışmaya yönelik araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cac5a-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="cac5a-104">Özelliklerini, yöntemlerini ve olaylarını oluşturma, kopyalama, taşıma, araştırmak ve dosya ve klasörleri silme için izin verin.</span><span class="sxs-lookup"><span data-stu-id="cac5a-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="cac5a-105">`My.Computer.FileSystem` eski işlevleri daha iyi performans sağlar (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, vs.), sağlanan Visual Basic tarafından geriye dönük uyumluluk için.</span><span class="sxs-lookup"><span data-stu-id="cac5a-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cac5a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cac5a-106">In This Section</span></span>  
 [<span data-ttu-id="cac5a-107">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="cac5a-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="cac5a-108">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` nesne dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="cac5a-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="cac5a-109">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="cac5a-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="cac5a-110">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` dosyalarına yazılacak nesne</span><span class="sxs-lookup"><span data-stu-id="cac5a-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="cac5a-111">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="cac5a-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="cac5a-112">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` oluşturma, kopyalama, silme ve taşıma dosyalar ve klasörler için nesne.</span><span class="sxs-lookup"><span data-stu-id="cac5a-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="cac5a-113">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="cac5a-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="cac5a-114">Nasıl kullanılacağı ele alınmaktadır `TextFieldReader` günlükleri gibi metin dosyalarını ayrıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="cac5a-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="cac5a-115">Dosya Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="cac5a-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="cac5a-116">Dosya kodlamaları ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cac5a-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="cac5a-117">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="cac5a-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="cac5a-118">Dosya ve klasörleri hakkında bilgi raporları bir yardımcı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cac5a-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="cac5a-119">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="cac5a-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="cac5a-120">Metin dosyaları için okuma ve yazma sırasında sık karşılaşılan sorunlar listeler ve her biri için çözümler önerir.</span><span class="sxs-lookup"><span data-stu-id="cac5a-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
