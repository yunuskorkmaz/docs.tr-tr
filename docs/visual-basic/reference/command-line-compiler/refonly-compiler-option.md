---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348571"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="3ba31-102">-Yalnızca ref(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ba31-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="3ba31-103">**-Refonly** seçeneği, derlemenin birincil çıktısının uygulama derlemesi yerine bir başvuru derlemesi olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ba31-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="3ba31-104">Başvuru derlemeleri yürütülene kadar `-refonly` parametresi, pdb 'leri çıktısını sessizce devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ba31-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="3ba31-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ba31-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="3ba31-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ba31-106">Remarks</span></span>

<span data-ttu-id="3ba31-107">Visual Basic, sürüm 15,3 ' den başlayarak `-refonly` anahtarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3ba31-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="3ba31-108">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="3ba31-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="3ba31-109">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="3ba31-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="3ba31-110">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="3ba31-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="3ba31-111">`-refonly` ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="3ba31-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ba31-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba31-112">See also</span></span>

- [<span data-ttu-id="3ba31-113">-refout</span><span class="sxs-lookup"><span data-stu-id="3ba31-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="3ba31-114">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3ba31-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3ba31-115">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3ba31-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
