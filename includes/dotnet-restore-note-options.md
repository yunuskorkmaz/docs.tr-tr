---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179974"
---
> [!NOTE]
> .NET Core 2,0 ' den başlayarak [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ' i çalıştırmanız gerekmez, çünkü `dotnet build` ve `dotnet run` gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırılır. Bir açık geri yüklemeyi yapmanın, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yükleme işleminin gerçekleştiği süreyi açıkça denetması gereken belirli senaryolarda geçerli bir komuttur.
>
> Bu komut, uzun biçimde geçirildiğinde `dotnet restore` seçeneklerini de destekler (örneğin, `--source`). @No__t-0 gibi kısa form seçenekleri desteklenmez.
