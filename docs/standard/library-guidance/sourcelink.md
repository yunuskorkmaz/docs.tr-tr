---
title: Kaynak Bağlantı ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için Kaynak Bağlantı kullanmak için en iyi uygulama önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744546"
---
# <a name="source-link"></a><span data-ttu-id="10b14-103">Kaynak Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="10b14-103">Source Link</span></span>

<span data-ttu-id="10b14-104">Kaynak Bağlantı geliştiriciler tarafından NuGet gelen .NET derlemeleri kaynak kodu hata ayıklama sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="10b14-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="10b14-105">Kaynak Bağlantısı, NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemelerin ve paketin içine yerlebir eder.</span><span class="sxs-lookup"><span data-stu-id="10b14-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="10b14-106">Paketi indiren ve Visual Studio'da Source Link'i etkinleştiren geliştiriciler, kaynak koduna adım atabilir.</span><span class="sxs-lookup"><span data-stu-id="10b14-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="10b14-107">Kaynak Bağlantı büyük bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="10b14-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="10b14-108">Kaynak Bağlantı demosu</span><span class="sxs-lookup"><span data-stu-id="10b14-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="10b14-109">Kaynak Bağlantısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="10b14-109">Using Source Link</span></span>

<span data-ttu-id="10b14-110">Kaynak Bağlantı'yı kullanma yönergeleri [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="10b14-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="10b14-111">Kaynak Bağlantı meta verilerinin pakete başarıyla yerleştirildiğini doğrulamak için [NuGet Paket](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) Gezgini'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10b14-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="10b14-112">Meta `Repository` verilerin bir işleme tanımlayıcısıyla mevcut olduğunu ve .pdb dosyalarının her hedefin .dll'si ile bulunduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10b14-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="10b14-113">![NuGet Paket Gezgini'nde Kaynak Bağlantı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgini'nde Kaynak Bağlantı")</span><span class="sxs-lookup"><span data-stu-id="10b14-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="10b14-114">✔️ Derlemelerinize ve NuGet paketlerinize kaynak denetimi meta verileri eklemek için Kaynak Bağlantısını kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="10b14-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="10b14-115">Türünüzüze hata ayıklama öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10b14-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="10b14-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>hata ayıklama değişkeni pencerelerinde bir sınıfın veya alanın nasıl görüntüleneceğini özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="10b14-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="10b14-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya koda adım atmak yerine kodu niçin geçmesi gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="10b14-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="10b14-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>bir üyenin hata ayıklama değişkeni penceresinde görüntülenip görüntülenmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="10b14-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="10b14-119">✔️ Simge dosyaları`*.pdb`yayımlama düşünün ( ).</span><span class="sxs-lookup"><span data-stu-id="10b14-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="10b14-120">En iyi hata ayıklama deneyimi için kitaplığınız sembol dosyaları yayımlamanın yanı sıra Kaynak Bağlantı'yı da kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10b14-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="10b14-121">Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için [Sembol paketlerine](./nuget.md#symbol-packages)bakın.</span><span class="sxs-lookup"><span data-stu-id="10b14-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="10b14-122">[Önceki](dependencies.md)
>[Sonraki](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="10b14-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
