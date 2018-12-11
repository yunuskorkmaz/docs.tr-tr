---
title: SourceLink ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için SourceLink kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128939"
---
# <a name="sourcelink"></a><span data-ttu-id="623cb-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="623cb-103">SourceLink</span></span>

<span data-ttu-id="623cb-104">SourceLink NuGet geliştiricilerin .NET derlemeleri, kaynak kodda hata ayıklama sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="623cb-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="623cb-105">SourceLink NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır.</span><span class="sxs-lookup"><span data-stu-id="623cb-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="623cb-106">Paketi indirebilir ve Visual Studio'da etkin SourceLink sahip geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="623cb-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="623cb-107">SourceLink harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="623cb-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="623cb-108">SourceLink Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="623cb-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="623cb-109">SourceLink kullanma</span><span class="sxs-lookup"><span data-stu-id="623cb-109">Using SourceLink</span></span>

<span data-ttu-id="623cb-110">SourceLink kullanımıyla ilgili yönergeleri bulunabilir [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="623cb-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="623cb-111">Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) SourceLink meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="623cb-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="623cb-112">Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.</span><span class="sxs-lookup"><span data-stu-id="623cb-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="623cb-113">![NuGet paket Gezgini'nde SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink, NuGet paket Gezgini")</span><span class="sxs-lookup"><span data-stu-id="623cb-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="623cb-114">**✔️ DÜŞÜNÜN** SourceLink kaynak denetimi meta verilerini, derlemeleri ve NuGet paketleri eklemek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="623cb-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="623cb-115">Türleriniz için hata ayıklayıcı öznitelikleri ekleyerek, geliştirici hata ayıklama deneyimi daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="623cb-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="623cb-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> bir sınıf ya da alan hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="623cb-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="623cb-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Hata ayıklayıcının kodun içine Adımlama yerine kod adım adım yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="623cb-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="623cb-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> üye hata ayıklayıcı değişken pencerelerinde görüntülenip görüntülenmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="623cb-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="623cb-119">**✔️ DÜŞÜNÜN** sembol dosyaları dahil olmak üzere (`*.pdb`) NuGet paketi olarak.</span><span class="sxs-lookup"><span data-stu-id="623cb-119">**✔️ CONSIDER** including symbol files (`*.pdb`) in the NuGet package.</span></span>

> <span data-ttu-id="623cb-120">Normalde, sembol dosyalarında yayımlamak istediğiniz bir [sembol paketi](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="623cb-120">Ordinarily, you'd publish symbol files in a [symbol package](./nuget.md#symbol-packages).</span></span> <span data-ttu-id="623cb-121">Sembol paketleri için genel ana taşınabilir sembol dosyaları şu anda desteklemiyor (`*.pdb`) SDK stili projeleri tarafından oluşturulan ve sembol paketleri kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="623cb-121">Currently the main public host for symbol packages doesn't support the portable symbol files (`*.pdb`) created by SDK-style projects, and symbol packages aren't useful.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="623cb-122">[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="623cb-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>