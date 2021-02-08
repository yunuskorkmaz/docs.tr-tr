---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic dosya oluşturma'
title: 'Nasıl yapılır: Dosya Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: b46786035c14021ceb27cce5b34eff5c8397fc9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797594"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="c3b2a-103">Nasıl Yapılır: Visual Basic'te Dosya Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c3b2a-103">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="c3b2a-104">Bu örnek, sınıfındaki yöntemini kullanarak belirtilen yolda boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="c3b2a-104">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b2a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3b2a-105">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3b2a-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c3b2a-106">Compiling the Code</span></span>  

 <span data-ttu-id="c3b2a-107">`file`Dosyaya yazmak için değişkenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c3b2a-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c3b2a-108">Robust Programming</span></span>  

 <span data-ttu-id="c3b2a-109">Dosya zaten varsa, değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="c3b2a-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c3b2a-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c3b2a-111">Yol adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-111">The path name is malformed.</span></span> <span data-ttu-id="c3b2a-112">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> ) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="c3b2a-113">Yol salt okunurdur ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="c3b2a-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="c3b2a-114">Yol adı `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="c3b2a-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="c3b2a-115">Yol adı çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="c3b2a-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="c3b2a-116">Yol geçersiz ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="c3b2a-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="c3b2a-117">Yol yalnızca bir iki nokta üst üste ":" ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="c3b2a-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c3b2a-118">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c3b2a-118">.NET Framework Security</span></span>  

 <span data-ttu-id="c3b2a-119"><xref:System.Security.SecurityException>Kısmi güven ortamlarında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="c3b2a-120">Yöntemine yapılan çağrı <xref:System.IO.File.Create%2A> gerekir <xref:System.Security.Permissions.FileIOPermission> .</span><span class="sxs-lookup"><span data-stu-id="c3b2a-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="c3b2a-121"><xref:System.UnauthorizedAccessException>Kullanıcının dosyayı oluşturma izni yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b2a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b2a-122">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="c3b2a-123">Kısmen Güvenilen Koddan Kitaplıkları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c3b2a-123">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="c3b2a-124">Kod Erişim Güvenliği Temelleri</span><span class="sxs-lookup"><span data-stu-id="c3b2a-124">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
