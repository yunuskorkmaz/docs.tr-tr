---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920729"
---

.NET Core paketini yüklerken, .'a `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`benzer bir hata görebilirsiniz. Genel olarak konuşursak, bu hata .NET Core'un paket akışının yeni paket sürümleriyle yükseltildiği ve daha sonra tekrar denemeniz gerektiği anlamına gelir. Yükseltme sırasında paket akışı 2 saatten fazla kullanılamaz. Bu hatayı sürekli olarak 2 saatten fazla alırsanız, <https://github.com/dotnet/core/issues>lütfen 'de bir sorun dosyalayın.
