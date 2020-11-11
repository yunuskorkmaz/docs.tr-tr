---
ms.openlocfilehash: 3bb59ba23214f67100d3a78bb689c941b2d187e6
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506992"
---

<span data-ttu-id="d4675-101">.NET paketini yüklerken buna benzer bir hata görebilirsiniz `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` .</span><span class="sxs-lookup"><span data-stu-id="d4675-101">While installing the .NET package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="d4675-102">Bu hata, .NET için paket akışı 'nın daha yeni paket sürümleriyle yükseltildiğini ve daha sonra yeniden denemeniz gerektiğini ifade etmelidir.</span><span class="sxs-lookup"><span data-stu-id="d4675-102">This error could mean that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="d4675-103">Yükseltme sırasında, paket akışı 30 dakikadan uzun bir süre için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="d4675-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="d4675-104">30 dakikadan uzun bir süre içinde sürekli olarak bu hatayı alırsanız, lütfen bir sorun bildirin <https://github.com/dotnet/core/issues> .</span><span class="sxs-lookup"><span data-stu-id="d4675-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
