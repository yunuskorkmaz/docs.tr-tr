---
ms.openlocfilehash: 5a027054024d8429831d73525ab3748c51ae850e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255768"
---

<span data-ttu-id="2c3c1-101">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2c3c1-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2c3c1-102">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2c3c1-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2c3c1-103">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="2c3c1-103">krb5-libs</span></span>
- <span data-ttu-id="2c3c1-104">libıu</span><span class="sxs-lookup"><span data-stu-id="2c3c1-104">libicu</span></span>
- <span data-ttu-id="2c3c1-105">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="2c3c1-105">openssl-libs</span></span>
- <span data-ttu-id="2c3c1-106">zlib</span><span class="sxs-lookup"><span data-stu-id="2c3c1-106">zlib</span></span>

<span data-ttu-id="2c3c1-107">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c3c1-107">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="2c3c1-108">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2c3c1-108">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="2c3c1-109">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="2c3c1-109">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="2c3c1-110">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="2c3c1-110">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="2c3c1-111">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c3c1-111">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2c3c1-112">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2c3c1-112">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
