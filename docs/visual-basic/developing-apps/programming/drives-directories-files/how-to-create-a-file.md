---
title: "Nasıl yapılır: Visual Basic'te dosya oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 397db70cc8f5977bd861e9e6d6df2f0c8f884db2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967023"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="79492-102">Nasıl yapılır: Visual Basic'te dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="79492-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="79492-103">Bu örnek, belirtilen yolu kullanarak boş bir metin dosyası oluşturur <xref:System.IO.File.Create%2A> yönteminde <xref:System.IO.File> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="79492-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79492-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="79492-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="79492-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="79492-105">Compiling the Code</span></span>  
 <span data-ttu-id="79492-106">Kullanım `file` dosyaya yazmak için değişken.</span><span class="sxs-lookup"><span data-stu-id="79492-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="79492-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="79492-107">Robust Programming</span></span>  
 <span data-ttu-id="79492-108">Dosya zaten varsa, değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="79492-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="79492-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="79492-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="79492-110">Yol adı yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="79492-110">The path name is malformed.</span></span> <span data-ttu-id="79492-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="79492-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="79492-112">Salt okunur yoludur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="79492-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="79492-113">Yol adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="79492-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="79492-114">Yol adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="79492-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="79492-115">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="79492-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="79492-116">Yalnızca bir iki nokta üst üste yoludur ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="79492-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="79492-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="79492-117">.NET Framework Security</span></span>  
 <span data-ttu-id="79492-118">A <xref:System.Security.SecurityException> kısmi güven düzeyine sahip ortamlarda oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="79492-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="79492-119">Çağrı <xref:System.IO.File.Create%2A> gerektirdiğine <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="79492-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="79492-120">Bir <xref:System.UnauthorizedAccessException> kullanıcının dosyayı oluşturma izni yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="79492-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79492-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79492-121">See also</span></span>
- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="79492-122">Kısmen güvenilen koddan kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="79492-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="79492-123">Kod erişimi güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="79492-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
