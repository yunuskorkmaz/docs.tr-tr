---
title: "Nasıl Yapılır: Visual Basic'te Dosya Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="9ab03-102">Nasıl Yapılır: Visual Basic'te Dosya Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ab03-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="9ab03-103">Bu örnek, belirtilen yolu kullanarak boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> yönteminde <xref:System.IO.File> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ab03-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab03-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ab03-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ab03-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9ab03-105">Compiling the Code</span></span>  
 <span data-ttu-id="9ab03-106">Kullanım `file` veya dosyaya yazmak için değişken.</span><span class="sxs-lookup"><span data-stu-id="9ab03-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9ab03-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9ab03-107">Robust Programming</span></span>  
 <span data-ttu-id="9ab03-108">Dosya zaten mevcutsa değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9ab03-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="9ab03-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="9ab03-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9ab03-110">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="9ab03-110">The path name is malformed.</span></span> <span data-ttu-id="9ab03-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="9ab03-112">Yolun salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="9ab03-113">Yol adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9ab03-114">Yol adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9ab03-115">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="9ab03-116">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9ab03-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9ab03-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9ab03-117">.NET Framework Security</span></span>  
 <span data-ttu-id="9ab03-118">A <xref:System.Security.SecurityException> kısmi güven ortamlarında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ab03-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="9ab03-119">Çağrı <xref:System.IO.File.Create%2A> gerektirdiğine <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="9ab03-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="9ab03-120">Bir <xref:System.UnauthorizedAccessException> kullanıcının dosyayı oluşturma izni yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ab03-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab03-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab03-121">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [<span data-ttu-id="9ab03-122">Kısmen güvenilen koddan kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="9ab03-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [<span data-ttu-id="9ab03-123">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="9ab03-123">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)
