---
title: -refout (C# derleyici seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771755"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="a536b-102">-refout (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a536b-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="a536b-103">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a536b-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="a536b-104">Bu, yayma API 'sindeki `metadataPeStream` çevirir.</span><span class="sxs-lookup"><span data-stu-id="a536b-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="a536b-105">Bu seçenek, MSBuild 'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a536b-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="a536b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a536b-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="a536b-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="a536b-107">Arguments</span></span>

 <span data-ttu-id="a536b-108">başvuru derlemesi için FilePath `filepath`.</span><span class="sxs-lookup"><span data-stu-id="a536b-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="a536b-109">Genellikle birincil derlemenin ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a536b-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="a536b-110">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="a536b-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="a536b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a536b-111">Remarks</span></span>

<span data-ttu-id="a536b-112">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="a536b-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="a536b-113">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="a536b-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="a536b-114">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="a536b-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="a536b-115">@No__t_0 ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="a536b-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="a536b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a536b-116">See also</span></span>

- [<span data-ttu-id="a536b-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a536b-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a536b-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a536b-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
