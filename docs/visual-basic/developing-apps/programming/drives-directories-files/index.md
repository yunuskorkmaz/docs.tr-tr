---
title: Sürücüleri, Dizinleri ve Dosyaları İşleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 0c9c1c787138595f725316a580acda9c5d4d43a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863630"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="b1ddc-102">Sürücüleri, Dizinleri ve Dosyaları İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1ddc-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="b1ddc-103">Visual Basic, sürücüler, klasörler ve dosyaları işlemek için kullanabileceğiniz `My.Computer.FileSystem` daha iyi performans sağlar ve gibi geleneksel yöntemlerinden daha kullanımı daha kolay olan nesne `FileOpen` ve `Write` (bunlar rağmen işlevleri kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="b1ddc-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="b1ddc-104">Aşağıdaki bölümlerde bu yöntemleri ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1ddc-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b1ddc-105">In This Section</span></span>  
 [<span data-ttu-id="b1ddc-106">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="b1ddc-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="b1ddc-107">Nasıl kullanılacağı ele alınmaktadır `My.Computer.FileSystem` dosyalarını, sürücülerini ve klasörleri ile çalışmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="b1ddc-108">.NET Framework dosyası g/ç ve dosya sistemi (Visual Basic) hakkında temel bilgiler</span><span class="sxs-lookup"><span data-stu-id="b1ddc-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="b1ddc-109">Akışlar, yalıtılmış depolama, dosya olayları, dosya öznitelikleri ve dosya erişimi de dahil olmak üzere .NET Framework dosyası g/ç kavramları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="b1ddc-110">İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="b1ddc-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="b1ddc-111">Nasıl kullanılacağını gösteren [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dosya ve klasörleri yönetmek için.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="b1ddc-112">İzlenecek yol: Dosyaları ve dizinleri Visual Basic'te düzenleme</span><span class="sxs-lookup"><span data-stu-id="b1ddc-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="b1ddc-113">Nasıl kullanılacağını gösteren `My.Computer.FileSystem` dosya ve klasörleri yönetmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b1ddc-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b1ddc-114">Related Sections</span></span>  
 [<span data-ttu-id="b1ddc-115">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="b1ddc-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="b1ddc-116">Fiziksel yapısı ve görüntüsüne programlar için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="b1ddc-117">Başvuru belgeleri için `My.Computer.FileSystem` nesne ve üyelerini.</span><span class="sxs-lookup"><span data-stu-id="b1ddc-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
