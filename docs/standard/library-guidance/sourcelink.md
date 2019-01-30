---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıkları için hata ayıklama geliştirmek için kaynak bağlantısı kullanılarak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 10596f589af7abee6ff7833ef25c606294337196
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204762"
---
# <a name="source-link"></a><span data-ttu-id="f9851-103">Kaynak bağlantısı</span><span class="sxs-lookup"><span data-stu-id="f9851-103">Source Link</span></span>

<span data-ttu-id="f9851-104">Kaynak bağlantısı kaynak geliştiriciler tarafından nuget'ten .NET bütünleştirilmiş kodda hata ayıklama sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="f9851-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="f9851-105">Kaynak bağlantısı NuGet paketini oluştururken yürütür ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırır.</span><span class="sxs-lookup"><span data-stu-id="f9851-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="f9851-106">Paketi indirebilir ve Visual Studio'da etkin kaynak bağlantısı olan geliştiriciler, kaynak kodunda adım adım ilerleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9851-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="f9851-107">Kaynak bağlantısı harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9851-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="f9851-108">Kaynak bağlantı Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="f9851-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="f9851-109">Kaynak bağlantısı kullanılarak</span><span class="sxs-lookup"><span data-stu-id="f9851-109">Using Source Link</span></span>

<span data-ttu-id="f9851-110">Kaynak bağlantısı kullanılarak yönergeler bulunabilir [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="f9851-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="f9851-111">Kullanabileceğiniz [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) kaynak bağlantısı meta verileri pakete başarıyla katıştırılmış olduğunu onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="f9851-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="f9851-112">Denetleme `Repository` açıklama tanımlayıcısına sahip meta veri varsa ve her hedefin .dll ile .pdb dosyaları bulunur.</span><span class="sxs-lookup"><span data-stu-id="f9851-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="f9851-113">![NuGet paket Gezgininde bağlantı kaynağı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet paket Gezgininde bağlantı kaynağı")</span><span class="sxs-lookup"><span data-stu-id="f9851-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="f9851-114">**✔️ DÜŞÜNÜN** kaynak denetimi meta verilerini, derlemeleri ve NuGet paketleri eklemek için kaynak bağlantısı kullanılarak.</span><span class="sxs-lookup"><span data-stu-id="f9851-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="f9851-115">Türleriniz için hata ayıklayıcı öznitelikleri ekleyerek, geliştirici hata ayıklama deneyimi daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9851-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="f9851-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> bir sınıf ya da alan hata ayıklayıcı değişken pencerelerinde nasıl görüntüleneceğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9851-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="f9851-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Hata ayıklayıcının kodun içine Adımlama yerine kod adım adım yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="f9851-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="f9851-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> üye hata ayıklayıcı değişken pencerelerinde görüntülenip görüntülenmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="f9851-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="f9851-119">**✔️ DÜŞÜNÜN** sembol dosyaları yayımlama (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="f9851-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="f9851-120">En iyi hata ayıklama deneyimi için kitaplığınızın pubish sembol dosyalarını gereken yanı sıra kaynak bağlantısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9851-120">For the best debugging experience your library should pubish symbol files as well as use Source Link.</span></span> <span data-ttu-id="f9851-121">Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="f9851-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f9851-122">[Önceki](dependencies.md)
>[İleri](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="f9851-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
