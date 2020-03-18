---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920644"
---

<span data-ttu-id="1c833-101">.NET Core paketini yüklerken, .'a `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`benzer bir hata görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c833-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="1c833-102">Genel olarak konuşursak, bu hata .NET Core'un paket akışının yeni paket sürümleriyle yükseltildiği ve daha sonra tekrar denemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1c833-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="1c833-103">Yükseltme sırasında paket akışı 30 dakikadan fazla kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1c833-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="1c833-104">Bu hatayı sürekli olarak 30 dakikadan fazla alırsanız, <https://github.com/dotnet/core/issues>lütfen 'de bir sorun dosyalayın.</span><span class="sxs-lookup"><span data-stu-id="1c833-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
