---
ms.openlocfilehash: 497ac09e5c9a10470d3ae1932d7e3dc114d121dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632001"
---
> [!NOTE]
> .NET Core 2.0 ile başlayarak, çalıştırma gerekmez [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) tüm komutlar tarafından gibi örtük olarak çalıştırıldığında çünkü `dotnet build` ve `dotnet run`, gerçekleşmesi için bir geri yükleme gerektirir. Bunu hala geçerli bir komut burada açık bir geri yükleme yaparsanız anlamlı, bazı senaryolarda olduğu gibi [sürekli tümleştirme derlemeleri Azure DevOps Hizmetleri'nde](/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya açıkça zaman denetlemek için gereken derleme sistemlerinde geri yükleme gerçekleşir.
>
> Bu komut ayrıca destekler `dotnet restore` seçenekleri uzun biçiminde geçirildiğinde (örneğin, `--source`). Form Seçenekleri gibi kısa `-s`, desteklenmez.
