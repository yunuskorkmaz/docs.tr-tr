---
ms.openlocfilehash: b371525c9f4e57c6a09e5bb9232884e5c5e707e0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603008"
---

<span data-ttu-id="8caab-101">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8caab-101">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="8caab-102">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8caab-102">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="8caab-103">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="8caab-103">lttng-ust</span></span>
- <span data-ttu-id="8caab-104">libkıvrık</span><span class="sxs-lookup"><span data-stu-id="8caab-104">libcurl</span></span>
- <span data-ttu-id="8caab-105">OpenSSL-libs</span><span class="sxs-lookup"><span data-stu-id="8caab-105">openssl-libs</span></span>
- <span data-ttu-id="8caab-106">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="8caab-106">krb5-libs</span></span>
- <span data-ttu-id="8caab-107">libıu</span><span class="sxs-lookup"><span data-stu-id="8caab-107">libicu</span></span>
- <span data-ttu-id="8caab-108">zlib</span><span class="sxs-lookup"><span data-stu-id="8caab-108">zlib</span></span>
- <span data-ttu-id="8caab-109">librüzgar</span><span class="sxs-lookup"><span data-stu-id="8caab-109">libunwind</span></span>
- <span data-ttu-id="8caab-110">libuuid</span><span class="sxs-lookup"><span data-stu-id="8caab-110">libuuid</span></span>

<span data-ttu-id="8caab-111">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8caab-111">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="8caab-112">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8caab-112">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="8caab-113">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="8caab-113">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="8caab-114">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="8caab-114">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="8caab-115">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8caab-115">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="8caab-116">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="8caab-116">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>
