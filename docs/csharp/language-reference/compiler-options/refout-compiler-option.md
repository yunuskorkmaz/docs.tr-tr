---
description: -refout (C# derleyici seçenekleri)
title: -refout (C# derleyici seçenekleri)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128720"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="884fc-103">-refout (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="884fc-103">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="884fc-104">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="884fc-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="884fc-105">Bu `metadataPeStream` , yayma API 'sine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="884fc-105">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="884fc-106">Bu seçenek, MSBuild 'in [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) Project özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="884fc-106">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="884fc-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="884fc-107">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="884fc-108">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="884fc-108">Arguments</span></span>

 <span data-ttu-id="884fc-109">`filepath` Başvuru derlemesinin FilePath 'i.</span><span class="sxs-lookup"><span data-stu-id="884fc-109">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="884fc-110">Genellikle birincil derlemenin ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="884fc-110">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="884fc-111">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="884fc-111">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="884fc-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="884fc-112">Remarks</span></span>

<span data-ttu-id="884fc-113">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="884fc-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="884fc-114">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="884fc-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="884fc-115">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="884fc-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="884fc-116">`-refout`Ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="884fc-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="884fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="884fc-117">See also</span></span>

- [<span data-ttu-id="884fc-118">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="884fc-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="884fc-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="884fc-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
