---
description: -delaysign (C# derleyici seçenekleri)
title: -delaysign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 5512ebeca4672f5d69852ab07c3f3fa40c305327
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125845"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="ce1f7-103">-delaysign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ce1f7-103">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="ce1f7-104">Bu seçenek derleyicinin çıkış dosyasında alan ayırmasını sağlayarak bir dijital imzanın daha sonra eklenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-104">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce1f7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ce1f7-105">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="ce1f7-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ce1f7-106">Arguments</span></span>

<span data-ttu-id="ce1f7-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ce1f7-107">`+` &#124; `-`</span></span>

<span data-ttu-id="ce1f7-108">Tam olarak imzalanan bir derlemeyi istiyorsanız **-delaysign-** kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-108">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="ce1f7-109">Yalnızca ortak anahtarı derlemeye yerleştirmek istiyorsanız **-delaysign +** kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-109">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="ce1f7-110">Varsayılan değer **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-110">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce1f7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce1f7-111">Remarks</span></span>

<span data-ttu-id="ce1f7-112">- [Keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmamışsa **-delaysign** seçeneğinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-112">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="ce1f7-113">**-Delaysign** ve **-publicsign** seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-113">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="ce1f7-114">Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="ce1f7-115">Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-115">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="ce1f7-116">Bir derlemenin gecikmesi gecikmeli kaydolduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenebilmesi için dosyada alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-116">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="ce1f7-117">Örneğin, **-delaysign +** kullanılması, bir sınayıcı 'ın derlemeyi genel önbellekte almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-117">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="ce1f7-118">Test ettikten sonra, derleme [bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tamamen imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-118">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="ce1f7-119">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="ce1f7-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ce1f7-120">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ce1f7-120">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="ce1f7-121">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-121">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="ce1f7-122">**Yalnızca gecikmeli imzala** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-122">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="ce1f7-123">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> ..</span><span class="sxs-lookup"><span data-stu-id="ce1f7-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce1f7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce1f7-124">See also</span></span>

- [<span data-ttu-id="ce1f7-125">C#-publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="ce1f7-125">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="ce1f7-126">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ce1f7-126">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="ce1f7-127">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ce1f7-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
