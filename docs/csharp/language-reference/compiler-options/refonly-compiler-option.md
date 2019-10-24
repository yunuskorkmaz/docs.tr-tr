---
title: -refonly (C# derleyici seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773848"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="e6a7d-102">-refonly (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e6a7d-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="e6a7d-103">**-Refonly** seçeneği, bir başvuru derlemesinin birincil çıktı olarak bir uygulama derlemesi yerine çıkış olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="e6a7d-104">Başvuru derlemeleri yürütülene kadar `-refonly` parametresi, pdb 'leri çıktısını sessizce devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="e6a7d-105">Bu seçenek, MSBuild 'in [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6a7d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6a7d-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="e6a7d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6a7d-107">Remarks</span></span>

<span data-ttu-id="e6a7d-108">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="e6a7d-109">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="e6a7d-110">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="e6a7d-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="e6a7d-111">@No__t_0 ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a7d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6a7d-112">See also</span></span>

- [<span data-ttu-id="e6a7d-113">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e6a7d-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e6a7d-114">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e6a7d-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
