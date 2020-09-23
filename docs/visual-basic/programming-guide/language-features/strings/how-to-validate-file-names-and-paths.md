---
title: 'Nasıl Yapılır: Dosya Adlarını ve Yollarını Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: b722222ea8b8088a6b326eef27147c08f8419272
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072658"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="b2982-102">Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="b2982-102">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="b2982-103">Bu örnek `Boolean` , bir dizenin bir dosya adı veya yolu temsil edip etmediğini gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2982-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="b2982-104">Doğrulama, adın dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="b2982-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2982-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2982-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b2982-106">Bu örnek, adın yanlış bir şekilde veya ada sahip olmayan dizinlerin mi yoksa ya da adın uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşarsa denetlemez.</span><span class="sxs-lookup"><span data-stu-id="b2982-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="b2982-107">Ayrıca, uygulamanın, belirtilen ada sahip dosya sistemi kaynağına erişme izni olup olmadığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="b2982-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2982-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2982-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="b2982-109">Visual Basic'de Dizeleri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="b2982-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
