---
title: "Nasıl yapılır: Visual Basic'te bir dizin oluşturun"
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: e94bd597b022e5e380651a62832e1f71fa72cec9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818715"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="3dcce-102">Nasıl yapılır: Visual Basic'te bir dizin oluşturun</span><span class="sxs-lookup"><span data-stu-id="3dcce-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="3dcce-103">Kullanım `CreateDirectory` yöntemi `My.Computer.FileSystem` dizinler oluşturmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="3dcce-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="3dcce-104">Dizin zaten varsa, hiçbir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3dcce-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="3dcce-105">Bir dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3dcce-105">To create a directory</span></span>  
  
-   <span data-ttu-id="3dcce-106">Kullanım `CreateDirectory` burada dizin oluşturulmalıdır konumun tam yolunu belirterek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3dcce-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="3dcce-107">Bu örnek dizini `NewDirectory` içinde `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="3dcce-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3dcce-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3dcce-108">Robust Programming</span></span>  
 <span data-ttu-id="3dcce-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="3dcce-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3dcce-110">Dizin adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="3dcce-110">The directory name is malformed.</span></span> <span data-ttu-id="3dcce-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="3dcce-112">Oluşturulacak dizinin üst dizin salt okunur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3dcce-113">Dizin adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="3dcce-114">Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="3dcce-115">Dizin adı iki nokta olan ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="3dcce-116">Kullanıcının dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="3dcce-117">Kullanıcı izinleri kısmi güven durumda eksik (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="3dcce-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dcce-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="3dcce-119">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="3dcce-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
