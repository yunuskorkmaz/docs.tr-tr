---
description: -Only (C# derleyici seçenekleri)
title: -Only (C# derleyici seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124753"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="4847c-103">-Only (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4847c-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="4847c-104">**-Refonly** seçeneği, bir başvuru derlemesinin birincil çıktı olarak bir uygulama derlemesi yerine çıkış olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4847c-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="4847c-105">`-refonly`Başvuru derlemeleri yürütülene kadar parametresi, pdb 'leri çıktısını yeniden devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4847c-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="4847c-106">Bu seçenek, MSBuild 'in [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4847c-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="4847c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4847c-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="4847c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4847c-108">Remarks</span></span>

<span data-ttu-id="4847c-109">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="4847c-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="4847c-110">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="4847c-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="4847c-111">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="4847c-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="4847c-112">`-refonly`Ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="4847c-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="4847c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4847c-113">See also</span></span>

- [<span data-ttu-id="4847c-114">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4847c-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4847c-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="4847c-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
