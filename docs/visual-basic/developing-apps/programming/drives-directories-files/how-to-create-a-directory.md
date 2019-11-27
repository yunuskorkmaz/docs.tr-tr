---
title: 'Nasıl Yapılır: Dizin Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348806"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="71d59-102">Nasıl Yapılır: Visual Basic'te Dizin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71d59-102">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="71d59-103">Dizinler oluşturmak için `My.Computer.FileSystem` nesnesinin `CreateDirectory` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="71d59-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="71d59-104">Dizin zaten varsa, hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="71d59-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="71d59-105">Bir dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71d59-105">To create a directory</span></span>  
  
- <span data-ttu-id="71d59-106">Dizinin oluşturulması gereken konumun tam yolunu belirterek `CreateDirectory` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="71d59-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="71d59-107">Bu örnek, Dizin `NewDirectory` `C:\Documents and Settings\All Users\Documents`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71d59-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="71d59-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="71d59-108">Robust Programming</span></span>  

 <span data-ttu-id="71d59-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="71d59-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="71d59-110">Dizin adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="71d59-110">The directory name is malformed.</span></span> <span data-ttu-id="71d59-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="71d59-112">Oluşturulacak dizinin üst dizini salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="71d59-113">Dizin adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="71d59-114">Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="71d59-115">Dizin adı iki nokta üst üste ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="71d59-116">Kullanıcının dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="71d59-117">Kullanıcının kısmi güven durumunda izinleri eksik (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="71d59-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d59-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71d59-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="71d59-119">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="71d59-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
