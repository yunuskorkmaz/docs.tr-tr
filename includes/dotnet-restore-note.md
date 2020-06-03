---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102754"
---
,,,, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) Ve gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırıldığı için çalıştırmanız gerekmez `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` `dotnet pack` . Örtük geri yüklemeyi devre dışı bırakmak için `--no-restore` seçeneğini kullanın.

`dotnet restore`Bu komut, açıkça geri yükleme işleminin, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yüklemenin ne zaman gerçekleşeceğini açıkça denetmasının gerektiği bazı senaryolarda de yararlıdır.

NuGet beslemelerini yönetme hakkında daha fazla bilgi için [ `dotnet restore` belgelerine](../docs/core/tools/dotnet-restore.md)bakın.
