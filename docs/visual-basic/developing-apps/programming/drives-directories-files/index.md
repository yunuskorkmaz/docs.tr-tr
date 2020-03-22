---
title: Sürücüleri, Dizinleri ve Dosyaları İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 790cf5aa2d3fde779fcc24c0c9f1fc9c4c42331b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333948"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="e7e14-102">Sürücüleri, Dizinleri ve Dosyaları İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7e14-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>

<span data-ttu-id="e7e14-103">Daha iyi performans sağlayan ve işlevleri `My.Computer.FileSystem` `FileOpen` (hala `Write` kullanılabilir olmalarına rağmen) gibi geleneksel yöntemlerden daha kolay olan sürücüleri, klasörleri ve dosyaları nesneyle işlemek için Visual Basic'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e14-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="e7e14-104">Aşağıdaki bölümlerde bu yöntemler ayrıntılı olarak tartışılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7e14-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7e14-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e7e14-105">In This Section</span></span>  

 [<span data-ttu-id="e7e14-106">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="e7e14-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="e7e14-107">Dosyalar, sürücüler ve `My.Computer.FileSystem` klasörlerle çalışmak için nesnenin nasıl kullanılacağını tartışır.</span><span class="sxs-lookup"><span data-stu-id="e7e14-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="e7e14-108">Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7e14-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="e7e14-109">Akışlar, yalıtılmış depolama, dosya olayları, dosya öznitelikleri ve dosya erişimi de dahil olmak üzere .NET Framework'deki dosya G/Ç kavramlarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e14-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="e7e14-110">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e7e14-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="e7e14-111">Dosya ve klasörleri işlemek için .NET Framework'ün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7e14-111">Demonstrates how to use the .NET Framework to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="e7e14-112">İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e7e14-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="e7e14-113">Dosya ve klasörleri `My.Computer.FileSystem` işlemek için nesnenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7e14-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7e14-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e7e14-114">Related Sections</span></span>  

 [<span data-ttu-id="e7e14-115">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="e7e14-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="e7e14-116">Programların fiziksel yapısı ve görünümü için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e14-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="e7e14-117">`My.Computer.FileSystem` Nesne ve üyeleri için başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="e7e14-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
