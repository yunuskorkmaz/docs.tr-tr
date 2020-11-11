---
ms.openlocfilehash: 8c05af045d2d9666b20f36e36c68cc853f906eae
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506875"
---

<span data-ttu-id="97418-101">.NET paketini yüklerken buna benzer bir hata görebilirsiniz `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'` .</span><span class="sxs-lookup"><span data-stu-id="97418-101">While installing the .NET package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="97418-102">Genellikle bu hata, .NET için paket beslemenin daha yeni paket sürümleriyle yükseltildiğini ve daha sonra yeniden denemeniz gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="97418-102">Generally speaking, this error means that the package feed for .NET is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="97418-103">Yükseltme sırasında, paket akışı 2 saatten uzun bir bir şekilde kullanılamıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97418-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="97418-104">Bu hatayı 2 saatten uzun bir zamanda alıyorsanız, lütfen bir sorun bildirin <https://github.com/dotnet/core/issues> .</span><span class="sxs-lookup"><span data-stu-id="97418-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
