---
title: "Nasıl Yapılır: Visual Basic'te Dizin Oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: ec9ee01e17f116e80708dbcb34e4d804bf3d7a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583961"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="71451-102">Nasıl Yapılır: Visual Basic'te Dizin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71451-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="71451-103">Kullanım `CreateDirectory` yöntemi `My.Computer.FileSystem` dizin oluşturmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="71451-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="71451-104">Dizini zaten varsa, hiçbir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="71451-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="71451-105">Bir dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71451-105">To create a directory</span></span>  
  
-   <span data-ttu-id="71451-106">Kullanım `CreateDirectory` burada dizin oluşturulmalıdır konumunun tam yolunu belirterek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71451-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="71451-107">Bu örnek dizinini oluşturur `NewDirectory` içinde `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="71451-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="71451-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="71451-108">Robust Programming</span></span>  
 <span data-ttu-id="71451-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="71451-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="71451-110">Dizin adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="71451-110">The directory name is malformed.</span></span> <span data-ttu-id="71451-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="71451-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="71451-112">Oluşturulacak dizininin üst dizini salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="71451-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="71451-113">Dizin adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="71451-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="71451-114">Dizin adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="71451-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="71451-115">Dizin adı bir iki nokta üst üste olan ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="71451-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="71451-116">Kullanıcının, dizin oluşturma izni yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="71451-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="71451-117">Kullanıcı bir kısmi güven durumda izinlerine sahip değildir (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="71451-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71451-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71451-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [<span data-ttu-id="71451-119">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="71451-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
