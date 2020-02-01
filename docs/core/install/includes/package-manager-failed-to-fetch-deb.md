---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920644"
---

<span data-ttu-id="d15a7-101">.NET Core paketini yüklerken `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`benzer bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d15a7-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="d15a7-102">Genellikle bu hata, .NET Core için paket akışı 'nın daha yeni paket sürümleriyle yükseltildiği ve daha sonra yeniden denemeniz gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d15a7-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="d15a7-103">Yükseltme sırasında, paket akışı 30 dakikadan uzun bir süre için kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="d15a7-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="d15a7-104">30 dakikadan uzun bir süre içinde sürekli olarak bu hatayı alırsanız lütfen <https://github.com/dotnet/core/issues>bir sorun bildirin.</span><span class="sxs-lookup"><span data-stu-id="d15a7-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
