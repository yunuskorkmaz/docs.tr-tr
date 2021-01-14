---
title: .NET için Azure SDK genel bakış
description: .NET için Azure SDK 'nın ne olduğuna ve bir .NET uygulamasında SDK 'Yı kullanmak için temel adımlara genel bakış sağlar
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b547e105b13d380ffae049ab55e76aa25abe8cc3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189206"
---
# <a name="azure-sdk-for-net-overview"></a>.NET için Azure SDK genel bakış

## <a name="what-is-the-azure-sdk-for-net"></a>.NET için Azure SDK nedir?

**.Net Için Azure SDK** , .NET uygulamalarınızdan Azure hizmetlerini kullanmayı kolaylaştırmak için tasarlanmıştır.  .NET için Azure SDK, Azure hizmetlerine erişmek için tutarlı ve tanıdık bir arabirim sağlar ve BLOB depolamaya dosya yükleme ve indirme, uygulama gizli dizileri Azure Key Vault veya Azure Event Hubs arasındaki bildirimleri işleme olup olmadığı.  

.NET için Azure SDK, hem .NET Core (2,1 ve üzeri) hem de .NET Framework (4.6.1 ve üzeri) uygulamalarda kullanılabilen NuGet paketleri serisi olarak sunulmaktadır.

![.NET uygulamalarının Azure hizmetlerine erişmek için Azure SDK 'sını nasıl kullandığını gösteren diyagram](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a>Uygulamalarınızda .NET için Azure SDK 'sını kullanın

.NET uygulamalarınızdan birinde bir Azure SDK paketi kullanmak için, bu adımları takip etmek istiyorsunuz.

1. **Uygun SDK paketini bulun-** Üzerinde çalıştığınız Azure hizmetine uygun paketi bulmak için [paket listesini](../packages.md) kullanın.  Çoğu hizmetin, hizmet ile birlikte çalışmak için bir istemci paketi ve hizmet örnekleri oluşturma ve yönetme için bir yönetim paketi olması önerilir.  Çoğu durumda, istemci paketini tercih edersiniz.  Bu paketi, NuGet kullanarak uygulamanıza yükler.

2. **Uygulamanız için kimlik doğrulamasını ayarlama-** Azure kaynaklarına erişmek için uygulamanızın Azure 'da atanmış uygun kimlik bilgilerine ve erişim haklarına sahip olması gerekir.  [.NET uygulamalarının](../authentication.md)kimlik doğrulamasını Azure 'da nasıl yapılandıracağınızı öğrenin.

3. **Uygulamanızdaki SDK 'yı kullanarak kod yazın-** Azure hizmetleriyle çalışırken kodunuz, önce hizmetle birlikte çalışmak üzere bir istemci nesnesi oluşturur ve sonra hizmetle etkileşimde bulunmak için bu istemci nesnesi üzerinde Yöntemler çağırır.  Hem zaman uyumlu hem de zaman uyumsuz yöntemler sağlanır.  Her bir SDK paketinin kullanılmasıyla ilgili örnekler, Azure belgelerinin tamamında sağlanır.

4. **SDK için günlüğü yapılandırma (isteğe bağlı)-** Uygulamanız ile Azure arasındaki sorunları tanılamanıza gerek duyuyorsanız, [.net Için Azure SDK 'da günlüğü etkinleştirebilirsiniz](../logging.md).
