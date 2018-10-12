---
title: SourceLink ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için SourceLink kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123879"
---
# <a name="sourcelink"></a><span data-ttu-id="af7f5-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="af7f5-103">SourceLink</span></span>

<span data-ttu-id="af7f5-104">SourceLink NuGet geliştiricilerin .NET derlemeleri, kaynak kodda hata ayıklama sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="af7f5-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="af7f5-105">SourceLink NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır.</span><span class="sxs-lookup"><span data-stu-id="af7f5-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="af7f5-106">Paketi indirebilir ve Visual Studio'da etkin SourceLink sahip geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af7f5-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="af7f5-107">SourceLink harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="af7f5-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="af7f5-108">SourceLink Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="af7f5-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="af7f5-109">SourceLink kullanma</span><span class="sxs-lookup"><span data-stu-id="af7f5-109">Using SourceLink</span></span>

<span data-ttu-id="af7f5-110">SourceLink kullanımıyla ilgili yönergeleri bulunabilir [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="af7f5-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="af7f5-111">Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) SourceLink meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="af7f5-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="af7f5-112">Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.</span><span class="sxs-lookup"><span data-stu-id="af7f5-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="af7f5-113">![NuGet paket Gezgini'nde SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink, NuGet paket Gezgini")</span><span class="sxs-lookup"><span data-stu-id="af7f5-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="af7f5-114">**✔️ DÜŞÜNÜN** SourceLink NuGet paketi ve derlemeler için kaynak denetimi meta verilerini eklemek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="af7f5-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

<span data-ttu-id="af7f5-115">**✔️ DÜŞÜNÜN** NuGet paketine PDB dosyaları.</span><span class="sxs-lookup"><span data-stu-id="af7f5-115">**✔️ CONSIDER** including PDB files in the NuGet package.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="af7f5-116">[Önceki](./dependencies.md)
[İleri](./publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="af7f5-116">[Previous](./dependencies.md)
[Next](./publish-nuget-package.md)</span></span>
