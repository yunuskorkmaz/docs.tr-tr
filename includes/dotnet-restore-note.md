---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2021
ms.locfileid: "90537748"
---
,,,, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) Ve gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırıldığı için çalıştırmanız gerekmez `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` `dotnet pack` . Örtük geri yüklemeyi devre dışı bırakmak için `--no-restore` seçeneğini kullanın.

`dotnet restore`Bu komut, açıkça geri yükleme işleminin, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yüklemenin ne zaman gerçekleşeceğini açıkça denetmasının gerektiği bazı senaryolarda de yararlıdır.

NuGet beslemelerini yönetme hakkında daha fazla bilgi için [ `dotnet restore` belgelerine](../docs/core/tools/dotnet-restore.md)bakın.
