---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179974"
---
> [!NOTE]
> .NET Core 2.0 ile başlayarak, geri [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) yükleme `dotnet build` gibi ve `dotnet run`. [Azure DevOps Hizmetleri'ndeki sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya geri yüklemenin gerçekleştiği zamanı açıkça denetlemesi gereken yapı sistemleri gibi açık bir geri yükleme yapmanın mantıklı olduğu belirli senaryolarda yine de geçerli bir komuttur.
>
> Bu komut, `dotnet restore` uzun formda geçirildiğinde (örneğin,) `--source`seçenekleri de destekler. Kısa form seçenekleri, `-s`örneğin, desteklenmez.
