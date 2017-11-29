---
title: "Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="5bbed-102">Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="5bbed-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="5bbed-103">Bu örnek döndüren bir `Boolean` bir dize bir dosya adı veya yolu temsil edip etmediğini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="5bbed-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="5bbed-104">Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="5bbed-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bbed-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bbed-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="5bbed-106">Bu örnek adı yanlış iki nokta üst üste veya dizinleri adı olmayan yerleştirdiğini veya adının uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez.</span><span class="sxs-lookup"><span data-stu-id="5bbed-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="5bbed-107">Bu da uygulama belirtilen ada sahip dosya sistemi kaynağa erişmek için izni olup olmadığını kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="5bbed-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbed-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5bbed-108">See Also</span></span>  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [<span data-ttu-id="5bbed-109">Visual Basic'de dizeleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="5bbed-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
