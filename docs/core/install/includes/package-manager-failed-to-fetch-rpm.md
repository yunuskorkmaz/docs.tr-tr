---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920729"
---

<span data-ttu-id="90864-101">.NET Core paketini yüklerken `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`benzer bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90864-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="90864-102">Genellikle bu hata, .NET Core için paket akışı 'nın daha yeni paket sürümleriyle yükseltildiği ve daha sonra yeniden denemeniz gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="90864-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="90864-103">Yükseltme sırasında, paket akışı 2 saatten uzun bir bir şekilde kullanılamıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90864-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="90864-104">Bu hatayı 2 saatten uzun bir zamanda alıyorsanız, lütfen <https://github.com/dotnet/core/issues>bir sorun bildirin.</span><span class="sxs-lookup"><span data-stu-id="90864-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
