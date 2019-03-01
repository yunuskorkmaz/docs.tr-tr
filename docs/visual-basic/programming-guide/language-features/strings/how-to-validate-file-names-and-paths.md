---
title: "Nasıl yapılır: Dosya adlarını ve yollarını Visual Basic'te doğrulama"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975530"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="22cff-102">Nasıl yapılır: Dosya adlarını ve yollarını Visual Basic'te doğrulama</span><span class="sxs-lookup"><span data-stu-id="22cff-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="22cff-103">Bu örnekte döndürür bir `Boolean` bir dizenin bir dosya adı veya yolu temsil edip etmediğini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="22cff-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="22cff-104">Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="22cff-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22cff-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="22cff-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="22cff-106">Bu örnekte, iki nokta üst üste veya dizin adı olmayan adı yanlış yerleştirdiğini veya adı sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez.</span><span class="sxs-lookup"><span data-stu-id="22cff-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="22cff-107">Bu da uygulamanın belirtilen ada sahip dosya sistemi kaynak erişim izni olup olmadığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="22cff-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22cff-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22cff-108">See also</span></span>
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="22cff-109">Visual Basic'de dizeleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="22cff-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
