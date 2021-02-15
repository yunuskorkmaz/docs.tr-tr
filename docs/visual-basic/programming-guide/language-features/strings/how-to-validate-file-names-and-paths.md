---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dosya adlarını ve yollarını doğrulama'
title: 'Nasıl Yapılır: Dosya Adlarını ve Yollarını Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429747"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="e4718-103">Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="e4718-103">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="e4718-104">Bu örnek `Boolean` , bir dizenin bir dosya adı veya yolu temsil edip etmediğini gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4718-104">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="e4718-105">Doğrulama, adın dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="e4718-105">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4718-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4718-106">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="e4718-107">Bu örnek, adın yanlış bir şekilde veya ada sahip olmayan dizinlerin mi yoksa ya da adın uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşarsa denetlemez.</span><span class="sxs-lookup"><span data-stu-id="e4718-107">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="e4718-108">Ayrıca, uygulamanın, belirtilen ada sahip dosya sistemi kaynağına erişme izni olup olmadığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="e4718-108">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4718-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4718-109">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="e4718-110">Visual Basic'de Dizeleri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="e4718-110">Validating Strings in Visual Basic</span></span>](validating-strings.md)
