---
title: Kaynak bağlantısı ve .NET kitaplıkları
description: .NET kitaplıklarında hata ayıklamayı geliştirmek için kaynak bağlantısını kullanmaya yönelik en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928985"
---
# <a name="source-link"></a><span data-ttu-id="2d45f-103">Kaynak Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="2d45f-103">Source Link</span></span>

<span data-ttu-id="2d45f-104">Kaynak bağlantısı, geliştiriciler tarafından NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="2d45f-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="2d45f-105">NuGet paketini oluştururken kaynak bağlantısı yürütülür ve derleme ve paket içindeki kaynak denetimi meta verilerini katıştırır.</span><span class="sxs-lookup"><span data-stu-id="2d45f-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="2d45f-106">Visual Studio 'da paketini indirir ve kaynak bağlantısı etkinleştirilmiş geliştiriciler, kaynak kodunu görebilir.</span><span class="sxs-lookup"><span data-stu-id="2d45f-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="2d45f-107">Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d45f-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="2d45f-108">Kaynak bağlantısı tanıtımı</span><span class="sxs-lookup"><span data-stu-id="2d45f-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="2d45f-109">Kaynak bağlantısı kullanma</span><span class="sxs-lookup"><span data-stu-id="2d45f-109">Using Source Link</span></span>

<span data-ttu-id="2d45f-110">Kaynak bağlantısı kullanma yönergeleri [DotNet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2d45f-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="2d45f-111">Kaynak bağlantısı meta verilerinin pakete başarıyla eklenmiş olduğunu doğrulamak için [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d45f-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="2d45f-112">`Repository` Meta verilerin bir açıklama tanımlayıcısı ile mevcut olduğunu ve bu. pdb dosyalarının her hedefin. dll ile bulunduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2d45f-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="2d45f-113">![NuGet Paket Gezgininde kaynak bağlantısı](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet Paket Gezgininde kaynak bağlantısı")</span><span class="sxs-lookup"><span data-stu-id="2d45f-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="2d45f-114">**✔️** derlemelerinize ve NuGet paketlerine kaynak denetimi meta verileri eklemek Için kaynak bağlantısı kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="2d45f-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="2d45f-115">Türlerinizi hata ayıklayıcı öznitelikleri ekleyerek bir geliştiricinin hata ayıklama deneyimini daha da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d45f-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="2d45f-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>, bir sınıfın veya alanın hata ayıklayıcı değişkeni penceresinde nasıl görüntülendiğini özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2d45f-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="2d45f-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>hata ayıklayıcıya koda Adımlama yerine kodda adım adım ilermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="2d45f-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="2d45f-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>hata ayıklayıcı değişkeni penceresinde bir üyenin görüntülenip görüntülenmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="2d45f-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="2d45f-119">**✔️** sembol dosyalarını yayımlamayı düşünün (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="2d45f-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="2d45f-120">En iyi hata ayıklama deneyimi için kitaplığınızın sembol dosyalarını yayımlaması ve kaynak bağlantısı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d45f-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="2d45f-121">Sembol dosyaları ve sembol paketleri hakkında daha fazla bilgi için bkz. [sembol paketleri](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="2d45f-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2d45f-122">[Önceki](dependencies.md)İleri
>[](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="2d45f-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
