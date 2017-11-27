---
title: "Visual Basic ile Dosya Erişimi"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9929061feeccee31028056bc93f0f0a2f119eb4e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="2ef63-102">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="2ef63-102">File Access with Visual Basic</span></span>
<span data-ttu-id="2ef63-103">`My.Computer.FileSystem` Nesnesi, dosyalar ve klasörlerle çalışmak için araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ef63-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="2ef63-104">Özellikleri, yöntemleri ve olayları oluşturma, kopyalama, taşıma, araştırmanıza ve dosya ve klasörleri silin sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ef63-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="2ef63-105">`My.Computer.FileSystem`eski işlevleri daha iyi performans sağlar (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, vs.) tarafından sağlanan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geriye dönük uyumluluk için.</span><span class="sxs-lookup"><span data-stu-id="2ef63-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ef63-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2ef63-106">In This Section</span></span>  
 [<span data-ttu-id="2ef63-107">Dosyaları okuma</span><span class="sxs-lookup"><span data-stu-id="2ef63-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="2ef63-108">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` nesne dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="2ef63-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="2ef63-109">Dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="2ef63-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="2ef63-110">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` dosyalarına yazılacak nesne</span><span class="sxs-lookup"><span data-stu-id="2ef63-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="2ef63-111">Oluşturma, silme ve dosyaları ve dizinleri taşıma</span><span class="sxs-lookup"><span data-stu-id="2ef63-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="2ef63-112">Kullanma ile ilgili konuları listeler `My.Computer.FileSystem` nesne oluşturma, kopyalama, silme ve taşıma dosyalar ve klasörler için.</span><span class="sxs-lookup"><span data-stu-id="2ef63-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="2ef63-113">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="2ef63-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="2ef63-114">Nasıl kullanılacağı açıklanır `TextFieldReader` günlükleri gibi metin dosyaları ayrıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2ef63-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="2ef63-115">Dosya kodlamaları</span><span class="sxs-lookup"><span data-stu-id="2ef63-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="2ef63-116">Dosya kodlamaları ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ef63-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="2ef63-117">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="2ef63-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="2ef63-118">Dosyalar ve klasörler hakkında bilgi raporları bir yardımcı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ef63-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="2ef63-119">Sorun giderme: Okuma ve dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="2ef63-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="2ef63-120">Metin dosyaları okuma ve yazma, sık karşılaşılan sorunlar listeler ve her çözümler önerir.</span><span class="sxs-lookup"><span data-stu-id="2ef63-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
