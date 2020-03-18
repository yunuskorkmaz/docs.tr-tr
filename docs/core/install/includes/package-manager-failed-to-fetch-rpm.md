---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920729"
---

<span data-ttu-id="5f92d-101">.NET Core paketini yüklerken, .'a `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`benzer bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f92d-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="5f92d-102">Genel olarak konuşursak, bu hata .NET Core'un paket akışının yeni paket sürümleriyle yükseltildiği ve daha sonra tekrar denemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5f92d-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="5f92d-103">Yükseltme sırasında paket akışı 2 saatten fazla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5f92d-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="5f92d-104">Bu hatayı sürekli olarak 2 saatten fazla alırsanız, <https://github.com/dotnet/core/issues>lütfen 'de bir sorun dosyalayın.</span><span class="sxs-lookup"><span data-stu-id="5f92d-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
