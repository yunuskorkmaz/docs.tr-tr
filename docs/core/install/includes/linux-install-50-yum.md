---
ms.openlocfilehash: cc394741e399f4fc54dd67f1736f7027badf4c7d
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507103"
---

### <a name="install-the-sdk"></a><span data-ttu-id="cd650-101">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="cd650-101">Install the SDK</span></span>

<span data-ttu-id="cd650-102">.NET SDK, .NET ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cd650-102">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="cd650-103">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cd650-103">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="cd650-104">.NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cd650-104">To install the .NET SDK, run the following commands:</span></span>

```bash
sudo yum install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="cd650-105">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="cd650-105">Install the runtime</span></span>

<span data-ttu-id="cd650-106">ASP.NET Core çalışma zamanı, .NET ile yapılan ve çalışma zamanı sağlamayan uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd650-106">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="cd650-107">Aşağıdaki komutlar, .NET için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="cd650-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="cd650-108">Terminalinizde aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cd650-108">In your terminal, run the following commands:</span></span>

```bash
sudo yum install aspnetcore-runtime-5.0
```

<span data-ttu-id="cd650-109">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-5.0` önceki komutta ile değiştirin `dotnet-runtime-5.0` :</span><span class="sxs-lookup"><span data-stu-id="cd650-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-5.0` in the previous command with `dotnet-runtime-5.0`:</span></span>

```bash
sudo yum install dotnet-runtime-5.0
```
