---
title: -refout (C# Derleyici Seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771755"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="eef07-102">-refout (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="eef07-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="eef07-103">**-refout** seçeneği, başvuru derlemesinin çıktı olması gereken bir dosya yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eef07-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="eef07-104">Bu Emit API `metadataPeStream` çevirir.</span><span class="sxs-lookup"><span data-stu-id="eef07-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="eef07-105">Bu seçenek, MSBuild'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) proje özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="eef07-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="eef07-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eef07-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="eef07-107">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="eef07-107">Arguments</span></span>

 <span data-ttu-id="eef07-108">`filepath`Başvuru derlemesi için dosya yolu.</span><span class="sxs-lookup"><span data-stu-id="eef07-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="eef07-109">Genellikle birincil derleme ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="eef07-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="eef07-110">Önerilen kural kuralı (MSBuild tarafından kullanılan) birincil derlemeye göre bir "ref/" alt klasörüne başvuru derlemesi yerleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="eef07-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="eef07-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eef07-111">Remarks</span></span>

<span data-ttu-id="eef07-112">Başvuru derlemeleri, kitaplığın genel API yüzeyini temsil etmek için gereken yalnızca minimum meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="eef07-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="eef07-113">Bunlar, yapı araçlarında bir derlemeye atıfta bulunurken önemli olan tüm üyeler için bildirimler içerir, ancak API sözleşmesi üzerinde gözlemlenebilir bir etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="eef07-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="eef07-114">Daha fazla bilgi için .NET Kılavuzu'ndaki [Başvuru derlemelerine](../../../standard/assembly/reference-assemblies.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="eef07-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="eef07-115">`-refout` Ve [`-refonly`](refonly-compiler-option.md) seçenekler birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="eef07-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="eef07-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eef07-116">See also</span></span>

- [<span data-ttu-id="eef07-117">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="eef07-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="eef07-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="eef07-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
