---
title: "'<functionname>' bildirilmedi (Akıllı Cihaz/Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 1c57e1aaea2eb52133d37b782f8fa0ddd96943a9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163408"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="8d30a-102">BC30766: ' \<functionname> ' bildirilmemiş (akıllı cihaz/Visual Basic derleyici hatası)</span><span class="sxs-lookup"><span data-stu-id="8d30a-102">BC30766: '\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="8d30a-103"><`functionname`> bildirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="8d30a-103"><`functionname`> is not declared.</span></span> <span data-ttu-id="8d30a-104">Dosya g/ç işlevselliği normalde `Microsoft.VisualBasic` ad alanında kullanılabilir, ancak .NET Compact Framework hedeflenen sürümü bunu desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8d30a-104">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>

 <span data-ttu-id="8d30a-105">**Hata kimliği:** BC30766</span><span class="sxs-lookup"><span data-stu-id="8d30a-105">**Error ID:** BC30766</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8d30a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8d30a-106">To correct this error</span></span>

- <span data-ttu-id="8d30a-107">Ad alanında tanımlanan işlevlerle dosya işlemleri gerçekleştirin `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="8d30a-107">Perform file operations with functions defined in the `System.IO` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d30a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d30a-108">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="8d30a-109">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="8d30a-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
