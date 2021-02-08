---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dizin oluşturma'
title: 'Nasıl yapılır: Dizin Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 39a0f1b2f482b27b6f207f0ca8a498db198e9d59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797607"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="8c6c7-103">Nasıl Yapılır: Visual Basic'te Dizin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c6c7-103">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="8c6c7-104">`CreateDirectory` `My.Computer.FileSystem` Dizin oluşturmak için nesnesinin yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-104">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="8c6c7-105">Dizin zaten varsa, hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-105">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="8c6c7-106">Bir dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8c6c7-106">To create a directory</span></span>  
  
- <span data-ttu-id="8c6c7-107">`CreateDirectory`Dizinin oluşturulması gereken konumun tam yolunu belirterek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-107">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="8c6c7-108">Bu örnek, dizininde dizinini `NewDirectory` oluşturur `C:\Documents and Settings\All Users\Documents` .</span><span class="sxs-lookup"><span data-stu-id="8c6c7-108">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8c6c7-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8c6c7-109">Robust Programming</span></span>  

 <span data-ttu-id="8c6c7-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8c6c7-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8c6c7-111">Dizin adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-111">The directory name is malformed.</span></span> <span data-ttu-id="8c6c7-112">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> ) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="8c6c7-113">Oluşturulacak dizinin üst dizini salt okunurdur ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8c6c7-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="8c6c7-114">Dizin adı `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="8c6c7-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="8c6c7-115">Dizin adı çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="8c6c7-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="8c6c7-116">Dizin adı iki nokta üst üste ":" ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="8c6c7-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="8c6c7-117">Kullanıcının dizin oluşturma izni yok ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="8c6c7-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="8c6c7-118">Kullanıcının kısmi güven durumunda () izinleri yoktur <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="8c6c7-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6c7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c6c7-119">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="8c6c7-120">Dosya ve Dizin Oluşturma, Silme ve Taşıma</span><span class="sxs-lookup"><span data-stu-id="8c6c7-120">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
