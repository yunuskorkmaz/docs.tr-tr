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
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="484ea-102">Nasıl Yapılır: Visual Basic'te Dosya Oluşturma</span><span class="sxs-lookup"><span data-stu-id="484ea-102">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="484ea-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span><span class="sxs-lookup"><span data-stu-id="484ea-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="484ea-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="484ea-104">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="484ea-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="484ea-105">Compiling the Code</span></span>  

 <span data-ttu-id="484ea-106">Use the `file` variable to write to the file.</span><span class="sxs-lookup"><span data-stu-id="484ea-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="484ea-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="484ea-107">Robust Programming</span></span>  

 <span data-ttu-id="484ea-108">If the file already exists, it is replaced.</span><span class="sxs-lookup"><span data-stu-id="484ea-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="484ea-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="484ea-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="484ea-110">The path name is malformed.</span><span class="sxs-lookup"><span data-stu-id="484ea-110">The path name is malformed.</span></span> <span data-ttu-id="484ea-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="484ea-112">The path is read-only (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="484ea-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="484ea-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="484ea-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="484ea-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="484ea-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="484ea-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="484ea-117">.NET Framework Security</span></span>  

 <span data-ttu-id="484ea-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span><span class="sxs-lookup"><span data-stu-id="484ea-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="484ea-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="484ea-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="484ea-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span><span class="sxs-lookup"><span data-stu-id="484ea-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484ea-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="484ea-121">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="484ea-122">Using Libraries from Partially Trusted Code</span><span class="sxs-lookup"><span data-stu-id="484ea-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="484ea-123">Code Access Security Basics</span><span class="sxs-lookup"><span data-stu-id="484ea-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
