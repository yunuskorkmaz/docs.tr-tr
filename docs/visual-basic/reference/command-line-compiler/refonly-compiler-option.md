---
description: Daha fazla bilgi edinin:-refonly (Visual Basic)
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 283aa75fceead38c62c4cf10c1ffe08151aeac9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474141"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="1f6a8-103">-Yalnızca ref(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f6a8-103">-refonly (Visual Basic)</span></span>

<span data-ttu-id="1f6a8-104">**-Refonly** seçeneği, derlemenin birincil çıktısının uygulama derlemesi yerine bir başvuru derlemesi olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-104">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="1f6a8-105">`-refonly`Başvuru derlemeleri yürütülene kadar parametresi, pdb 'leri çıktısını yeniden devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="1f6a8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f6a8-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="1f6a8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f6a8-107">Remarks</span></span>

<span data-ttu-id="1f6a8-108">Visual Basic, `-refonly` sürüm 15,3 ' den başlayarak anahtarı destekler.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-108">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="1f6a8-109">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="1f6a8-110">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="1f6a8-111">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="1f6a8-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="1f6a8-112">`-refonly`Ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f6a8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6a8-113">See also</span></span>

- [<span data-ttu-id="1f6a8-114">-refout</span><span class="sxs-lookup"><span data-stu-id="1f6a8-114">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="1f6a8-115">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1f6a8-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1f6a8-116">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="1f6a8-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
