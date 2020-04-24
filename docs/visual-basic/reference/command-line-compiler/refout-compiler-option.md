---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348649"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="05db3-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05db3-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="05db3-103">**-Refout** seçeneği, başvuru derlemesinin çıkış olması gereken bir dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="05db3-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="05db3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05db3-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="05db3-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="05db3-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="05db3-106">Başvuru derlemesinin yolu ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="05db3-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="05db3-107">Genellikle birincil derlemenin alt klasöründe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05db3-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="05db3-108">Önerilen kural (MSBuild tarafından kullanılır), başvuru derlemesini birincil derlemeye göre bir "ref/" alt klasörüne yerleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="05db3-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="05db3-109">İçindeki `filepath` tüm klasörler var olmalıdır; derleyici bunları oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="05db3-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="05db3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05db3-110">Remarks</span></span>

<span data-ttu-id="05db3-111">Visual Basic, `-refout` sürüm 15,3 ' den başlayarak anahtarı destekler.</span><span class="sxs-lookup"><span data-stu-id="05db3-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="05db3-112">Başvuru derlemeleri, kitaplığın ortak API yüzeyini göstermek için gereken en düşük meta veri miktarını içeren özel bir derleme türüdür.</span><span class="sxs-lookup"><span data-stu-id="05db3-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="05db3-113">Derleme araçlarındaki bir derlemeye başvururken önemli olan tüm Üyeler için bildirimler içerirler, ancak API sözleşmeleri üzerinde herhangi bir observable etkisi olmayan özel üyelerin tüm üye uygulamalarını ve bildirimlerini hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="05db3-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="05db3-114">Daha fazla bilgi için bkz. .NET kılavuzundaki [başvuru derlemeleri](../../../standard/assembly/reference-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="05db3-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="05db3-115">`-refout` Ve [`-refonly`](refonly-compiler-option.md) seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="05db3-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="05db3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05db3-116">See also</span></span>

- [<span data-ttu-id="05db3-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="05db3-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="05db3-118">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="05db3-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="05db3-119">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="05db3-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
