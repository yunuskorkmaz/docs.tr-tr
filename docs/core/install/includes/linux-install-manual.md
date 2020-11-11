---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506823"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="cdb69-101">Paket yöneticilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdb69-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="cdb69-102">El ile yüklemeyi genellikle sürekli tümleştirme testi kapsamında veya desteklenmeyen bir Linux dağıtımında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cdb69-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="cdb69-103">Bir geliştirici veya Kullanıcı için genellikle bir paket yöneticisi kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="cdb69-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="cdb69-104">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cdb69-104">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="cdb69-105">İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:</span><span class="sxs-lookup"><span data-stu-id="cdb69-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="cdb69-106">✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="cdb69-106">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="cdb69-107">✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="cdb69-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="cdb69-108">✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="cdb69-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="cdb69-109">Tüm .NET Core İndirmeleri</span><span class="sxs-lookup"><span data-stu-id="cdb69-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="cdb69-110">Ardından, indirilen dosyayı ayıklayın ve `export` .NET tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .net 'ın yol içinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cdb69-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="cdb69-111">Çalışma zamanını ayıklamak ve .NET CLı komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET ikili sürümü indirin.</span><span class="sxs-lookup"><span data-stu-id="cdb69-111">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="cdb69-112">Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cdb69-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="cdb69-113">Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cdb69-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="cdb69-114">**Çalışma zamanını ayıklamak için aşağıdaki komutu kullanın** :</span><span class="sxs-lookup"><span data-stu-id="cdb69-114">**Use the following command to extract the runtime** :</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="cdb69-115">**SDK 'yı ayıklamak için aşağıdaki komutu kullanın** :</span><span class="sxs-lookup"><span data-stu-id="cdb69-115">**Use the following command to extract the SDK** :</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="cdb69-116">Yukarıdaki `export` Komutlar yalnızca .net CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="cdb69-116">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="cdb69-117">Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdb69-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="cdb69-118">Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="cdb69-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="cdb69-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cdb69-119">For example:</span></span>
>
> - <span data-ttu-id="cdb69-120">**Bash kabuğu** : *~/.bash_profile* , *~/,bashrc*</span><span class="sxs-lookup"><span data-stu-id="cdb69-120">**Bash Shell** : *~/.bash_profile* , *~/.bashrc*</span></span>
> - <span data-ttu-id="cdb69-121">**Korn kabuğu** : *~/,KSHRC* veya *. Profile*</span><span class="sxs-lookup"><span data-stu-id="cdb69-121">**Korn Shell** : *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="cdb69-122">**Z kabuğu** : *~/,zshrc* veya *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="cdb69-122">**Z Shell** : *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="cdb69-123">Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` .</span><span class="sxs-lookup"><span data-stu-id="cdb69-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="cdb69-124">Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="cdb69-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="cdb69-125">Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdb69-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="cdb69-126">Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cdb69-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
