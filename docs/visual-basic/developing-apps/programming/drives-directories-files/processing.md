---
title: Sürücüleri, Dizinleri ve Dosyaları İşleme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aad7ea3a24bf0f738999c58a7934d1ffcf92b967
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="e1b2e-102">Sürücüleri, Dizinleri ve Dosyaları İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1b2e-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="e1b2e-103">Visual Basic sürücüler, klasörler ve dosyalar ile işlemek için kullanabileceğiniz `My.Computer.FileSystem` daha iyi performans sağlar ve gibi geleneksel yöntemlerini kullanmayı daha kolay olan nesne, `FileOpen` ve `Write` (bunlar hala olmasına rağmen işlevleri kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="e1b2e-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="e1b2e-104">Aşağıdaki bölümlerde bu yöntemleri ayrıntılı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1b2e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e1b2e-105">In This Section</span></span>  
 [<span data-ttu-id="e1b2e-106">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="e1b2e-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="e1b2e-107">Nasıl kullanılacağı açıklanır `My.Computer.FileSystem` dosyalarını, sürücülerini ve klasörleri ile çalışmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="e1b2e-108">.NET Framework dosyası g/ç ve dosya sistemi (Visual Basic) Temelleri</span><span class="sxs-lookup"><span data-stu-id="e1b2e-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="e1b2e-109">Akışlar, yalıtılmış depolama, dosya olayları, dosya öznitelikleri ve dosya erişimi de dahil olmak üzere, .NET Framework dosyası g/ç kavramlarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="e1b2e-110">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e1b2e-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="e1b2e-111">Nasıl kullanılacağı ortaya [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dosya ve klasörleri yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="e1b2e-112">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="e1b2e-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="e1b2e-113">Nasıl kullanılacağı ortaya `My.Computer.FileSystem` dosya ve klasörleri işlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1b2e-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e1b2e-114">Related Sections</span></span>  
 [<span data-ttu-id="e1b2e-115">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="e1b2e-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="e1b2e-116">Yönergeleri fiziksel yapısı ve programları görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="e1b2e-117">Başvuru belgelerini için `My.Computer.FileSystem` nesne ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="e1b2e-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
