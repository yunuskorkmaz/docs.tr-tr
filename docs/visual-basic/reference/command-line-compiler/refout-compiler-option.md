---
description: Daha fazla bilgi edinin:-refout (Visual Basic)
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 2760f7e60d950aaff90becad843824a2e2b4379f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474128"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="d1085-103">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1085-103">-refout (Visual Basic)</span></span>

<span data-ttu-id="d1085-104">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d1085-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="d1085-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1085-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="d1085-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d1085-106">Arguments</span></span>

`filepath`  
<span data-ttu-id="d1085-107">Başvuru derlemesinin yolu ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="d1085-107">The path and filename of the reference assembly.</span></span> <span data-ttu-id="d1085-108">Genellikle birincil derlemenin alt klasöründe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1085-108">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="d1085-109">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="d1085-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="d1085-110">İçindeki tüm klasörler `filepath` var olmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d1085-110">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1085-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1085-111">Remarks</span></span>

<span data-ttu-id="d1085-112">Visual Basic, `-refout` sürüm 15,3 ' den başlayarak anahtarı destekler.</span><span class="sxs-lookup"><span data-stu-id="d1085-112">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="d1085-113">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="d1085-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="d1085-114">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="d1085-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="d1085-115">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="d1085-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="d1085-116">`-refout`Ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="d1085-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1085-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1085-117">See also</span></span>

- [<span data-ttu-id="d1085-118">-refonly</span><span class="sxs-lookup"><span data-stu-id="d1085-118">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="d1085-119">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d1085-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d1085-120">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d1085-120">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
