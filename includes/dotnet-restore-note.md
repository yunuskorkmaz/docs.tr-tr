---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102754"
---
Geri yükleme yapılmasını gerektiren [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) tüm komutlar tarafından örtülü olarak çalıştırıldığı için çalıştırmak zorunda `dotnet new` `dotnet build`değilsiniz, `dotnet publish`, `dotnet pack`, `dotnet run` `dotnet test`, , ve . Örtülü geri yüklemeyi devre `--no-restore` dışı kalmak için seçeneği kullanın.

Komut, `dotnet restore` [Azure DevOps Hizmetleri'ndeki sürekli tümleştirme yapıları](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) veya geri yükleme nin ne zaman gerçekleşacağını açıkça denetlemesi gereken yapı sistemleri gibi açıkça geri yüklemenin mantıklı olduğu belirli senaryolarda yine de yararlıdır.

NuGet akışlarının nasıl yönetilenhakkında bilgi için [ `dotnet restore` belgelere](../docs/core/tools/dotnet-restore.md)bakın.
