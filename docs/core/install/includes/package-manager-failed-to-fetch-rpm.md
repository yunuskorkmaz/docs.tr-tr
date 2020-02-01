---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920729"
---

.NET Core paketini yüklerken `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`benzer bir hata görebilirsiniz. Genellikle bu hata, .NET Core için paket akışı 'nın daha yeni paket sürümleriyle yükseltildiği ve daha sonra yeniden denemeniz gereken anlamına gelir. Yükseltme sırasında, paket akışı 2 saatten uzun bir bir şekilde kullanılamıyor olmalıdır. Bu hatayı 2 saatten uzun bir zamanda alıyorsanız, lütfen <https://github.com/dotnet/core/issues>bir sorun bildirin.
