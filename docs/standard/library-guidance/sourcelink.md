---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıklarında hata ayıklamayı geliştirmek için kaynak bağlantısını kullanmaya yönelik en iyi yöntem önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744546"
---
# <a name="source-link"></a><span data-ttu-id="59d9a-103">Kaynak Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="59d9a-103">Source Link</span></span>

<span data-ttu-id="59d9a-104">Kaynak bağlantısı, geliştiriciler tarafından NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="59d9a-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="59d9a-105">NuGet paketini oluştururken kaynak bağlantısı yürütülür ve derleme ve paket içindeki kaynak denetimi meta verilerini katıştırır.</span><span class="sxs-lookup"><span data-stu-id="59d9a-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="59d9a-106">Visual Studio 'da paketini indirir ve kaynak bağlantısı etkinleştirilmiş geliştiriciler, kaynak kodunu görebilir.</span><span class="sxs-lookup"><span data-stu-id="59d9a-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="59d9a-107">Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="59d9a-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="59d9a-108">Kaynak bağlantısı tanıtımı</span><span class="sxs-lookup"><span data-stu-id="59d9a-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="59d9a-109">Kaynak bağlantısı kullanma</span><span class="sxs-lookup"><span data-stu-id="59d9a-109">Using Source Link</span></span>

<span data-ttu-id="59d9a-110">Kaynak bağlantısı kullanma yönergeleri [DotNet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="59d9a-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="59d9a-111">Kaynak bağlantısı meta verilerinin pakete başarıyla eklenmiş olduğunu doğrulamak için [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59d9a-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="59d9a-112">`Repository` meta verilerin bir COMMIT tanımlayıcısı ile mevcut olduğunu ve bu. pdb dosyalarının her hedefin. dll ile bulunduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="59d9a-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="59d9a-113">![NuGet Paket Gezgininde kaynak bağlantısı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgininde kaynak bağlantısı")</span><span class="sxs-lookup"><span data-stu-id="59d9a-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="59d9a-114">✔️ derlemelerinize ve NuGet paketlerine kaynak denetimi meta verileri eklemek için kaynak bağlantısı kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="59d9a-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="59d9a-115">Türlerinizi hata ayıklayıcı öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59d9a-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="59d9a-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>, bir sınıfın veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="59d9a-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="59d9a-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>, hata ayıklayıcıya koda adımla değil kodun içinde ilermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="59d9a-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="59d9a-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>, bir üyenin hata ayıklayıcı değişken pencerelerinin görüntülenip görüntülenmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="59d9a-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="59d9a-119">✔️ sembol dosyalarını yayımlamayı düşünün (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="59d9a-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="59d9a-120">En iyi hata ayıklama deneyimi için kitaplığınızın sembol dosyalarını yayımlaması ve kaynak bağlantısı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="59d9a-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="59d9a-121">Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="59d9a-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="59d9a-122">[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="59d9a-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
