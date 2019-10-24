---
title: -Yalnızca ref(Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775560"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="f2df8-102">-Yalnızca ref(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2df8-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="f2df8-103">**-Refonly** seçeneği, derlemenin birincil çıktısının uygulama derlemesi yerine bir başvuru derlemesi olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2df8-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="f2df8-104">Başvuru derlemeleri yürütülene kadar `-refonly` parametresi, pdb 'leri çıktısını sessizce devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f2df8-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="f2df8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2df8-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="f2df8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2df8-106">Remarks</span></span>

<span data-ttu-id="f2df8-107">Visual Basic, sürüm 15,3 ' den başlayarak `-refonly` anahtarını destekler.</span><span class="sxs-lookup"><span data-stu-id="f2df8-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="f2df8-108">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="f2df8-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="f2df8-109">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="f2df8-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="f2df8-110">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="f2df8-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="f2df8-111">@No__t_0 ve [`-refout`](refout-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="f2df8-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2df8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2df8-112">See also</span></span>

- [<span data-ttu-id="f2df8-113">-refout</span><span class="sxs-lookup"><span data-stu-id="f2df8-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="f2df8-114">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f2df8-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f2df8-115">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="f2df8-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
