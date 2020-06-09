---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602980"
---

<span data-ttu-id="045f7-101">.NET Core paketini yüklerken buna benzer bir hata görebilirsiniz `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` .</span><span class="sxs-lookup"><span data-stu-id="045f7-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="045f7-102">Bu hata, .NET Core için paket akışı 'nın daha yeni paket sürümleriyle yükseltilmekte olduğunu ve daha sonra yeniden denemeniz gerektiğini ifade etmelidir.</span><span class="sxs-lookup"><span data-stu-id="045f7-102">This error could mean that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="045f7-103">Yükseltme sırasında, paket akışı 30 dakikadan uzun bir süre için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="045f7-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="045f7-104">30 dakikadan uzun bir süre içinde sürekli olarak bu hatayı alırsanız, lütfen bir sorun bildirin <https://github.com/dotnet/core/issues> .</span><span class="sxs-lookup"><span data-stu-id="045f7-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
