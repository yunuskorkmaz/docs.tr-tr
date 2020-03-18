---
title: -refonly (C# Derleyici Seçenekleri)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773848"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="530e4-102">-refonly (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="530e4-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="530e4-103">**-refonly** seçeneği, birincil çıktı olarak bir uygulama derlemesi yerine bir başvuru derlemesinin çıktı olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="530e4-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="530e4-104">`-refonly` Parametre, başvuru derlemeleri yürütülemediği için PDB'leri sessizce devre dışı bıraktı.</span><span class="sxs-lookup"><span data-stu-id="530e4-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="530e4-105">Bu seçenek, MSBuild'in [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) proje özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="530e4-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="530e4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="530e4-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="530e4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="530e4-107">Remarks</span></span>

<span data-ttu-id="530e4-108">Başvuru derlemeleri, kitaplığın genel API yüzeyini temsil etmek için gereken yalnızca minimum meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="530e4-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="530e4-109">Bunlar, yapı araçlarında bir derlemeye atıfta bulunurken önemli olan tüm üyeler için bildirimler içerir, ancak API sözleşmesi üzerinde gözlemlenebilir bir etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="530e4-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="530e4-110">Daha fazla bilgi için .NET Kılavuzu'ndaki [Başvuru derlemelerine](../../../standard/assembly/reference-assemblies.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="530e4-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="530e4-111">`-refonly` Ve [`-refout`](refout-compiler-option.md) seçenekler birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="530e4-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="530e4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="530e4-112">See also</span></span>

- [<span data-ttu-id="530e4-113">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="530e4-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="530e4-114">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="530e4-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
