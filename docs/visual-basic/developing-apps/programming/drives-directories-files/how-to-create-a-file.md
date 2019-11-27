---
title: 'Nasıl Yapılır: Dosya Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348792"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="f59c6-102">Nasıl Yapılır: Visual Basic'te Dosya Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f59c6-102">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="f59c6-103">Bu örnek, <xref:System.IO.File> sınıfındaki <xref:System.IO.File.Create%2A> yöntemi kullanılarak belirtilen yolda boş bir metin dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f59c6-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f59c6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f59c6-104">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f59c6-105">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="f59c6-105">Compiling the Code</span></span>  

 <span data-ttu-id="f59c6-106">Dosyaya yazmak için `file` değişkenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f59c6-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f59c6-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f59c6-107">Robust Programming</span></span>  

 <span data-ttu-id="f59c6-108">Dosya zaten varsa, değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f59c6-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="f59c6-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f59c6-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f59c6-110">Yol adı hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f59c6-110">The path name is malformed.</span></span> <span data-ttu-id="f59c6-111">Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f59c6-112">Yol salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f59c6-113">Yol adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f59c6-114">Yol adı çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f59c6-115">Yol geçersiz (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f59c6-116">Yol yalnızca bir iki nokta üst üste ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f59c6-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f59c6-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f59c6-117">.NET Framework Security</span></span>  

 <span data-ttu-id="f59c6-118">Kısmi güven ortamlarında bir <xref:System.Security.SecurityException> oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f59c6-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="f59c6-119"><xref:System.IO.File.Create%2A> metoduna yapılan çağrı <xref:System.Security.Permissions.FileIOPermission>gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f59c6-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="f59c6-120">Kullanıcının dosyayı oluşturma izni yoksa bir <xref:System.UnauthorizedAccessException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f59c6-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59c6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f59c6-121">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="f59c6-122">Kısmen güvenilen koddan kitaplıkları kullanma</span><span class="sxs-lookup"><span data-stu-id="f59c6-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="f59c6-123">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="f59c6-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
