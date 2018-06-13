---
title: "Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647810"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="82952-102">Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="82952-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="82952-103">Bu örnek döndüren bir `Boolean` bir dize bir dosya adı veya yolu temsil edip etmediğini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="82952-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="82952-104">Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="82952-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82952-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="82952-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="82952-106">Bu örnek adı yanlış iki nokta üst üste veya dizinleri adı olmayan yerleştirdiğini veya adının uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez.</span><span class="sxs-lookup"><span data-stu-id="82952-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="82952-107">Bu da uygulama belirtilen ada sahip dosya sistemi kaynağa erişmek için izni olup olmadığını kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="82952-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82952-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82952-108">See Also</span></span>  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [<span data-ttu-id="82952-109">Visual Basic'de dizeleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="82952-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
