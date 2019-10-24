---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775555"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="7ff3a-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ff3a-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="7ff3a-103">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="7ff3a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ff3a-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="7ff3a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7ff3a-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="7ff3a-106">Başvuru derlemesinin yolu ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="7ff3a-107">Genellikle birincil derlemenin alt klasöründe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="7ff3a-108">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="7ff3a-109">@No__t_0 tüm klasörler var olmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ff3a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ff3a-110">Remarks</span></span>

<span data-ttu-id="7ff3a-111">Visual Basic, sürüm 15,3 ' den başlayarak `-refout` anahtarını destekler.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="7ff3a-112">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="7ff3a-113">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="7ff3a-114">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="7ff3a-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="7ff3a-115">@No__t_0 ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ff3a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff3a-116">See also</span></span>

- [<span data-ttu-id="7ff3a-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="7ff3a-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="7ff3a-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7ff3a-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7ff3a-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7ff3a-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
