---
title: -delaysign (C# derleyici seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: ae309a8de6c4691f0009e5beb8ac2adc8772805b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603030"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="41c32-102">-delaysign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="41c32-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="41c32-103">Bu seçenek derleyicinin çıkış dosyasında alan ayırmasını sağlayarak bir dijital imzanın daha sonra eklenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="41c32-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="41c32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41c32-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="41c32-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="41c32-105">Arguments</span></span>

<span data-ttu-id="41c32-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="41c32-106">`+` &#124; `-`</span></span>

<span data-ttu-id="41c32-107">Tam olarak imzalanan bir derlemeyi istiyorsanız **-delaysign-** kullanın.</span><span class="sxs-lookup"><span data-stu-id="41c32-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="41c32-108">Yalnızca ortak anahtarı derlemeye yerleştirmek istiyorsanız **-delaysign +** kullanın.</span><span class="sxs-lookup"><span data-stu-id="41c32-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="41c32-109">Varsayılan değer **-delaysign-** .</span><span class="sxs-lookup"><span data-stu-id="41c32-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="41c32-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41c32-110">Remarks</span></span>

<span data-ttu-id="41c32-111">\- [Keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmamışsa **-delaysign** seçeneğinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="41c32-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="41c32-112">**-Delaysign** ve **-publicsign** seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="41c32-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="41c32-113">Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="41c32-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="41c32-114">Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41c32-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="41c32-115">Bir derlemenin gecikmesi gecikmeli kaydolduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenebilmesi için dosyada alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="41c32-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="41c32-116">Örneğin, **-delaysign +** kullanılması, bir sınayıcı 'ın derlemeyi genel önbellekte almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="41c32-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="41c32-117">Test ettikten sonra, derleme [bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tamamen imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41c32-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="41c32-118">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [bir derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="41c32-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="41c32-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="41c32-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="41c32-120">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="41c32-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="41c32-121">**Yalnızca gecikmeli imzala** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41c32-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="41c32-122">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="41c32-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="41c32-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c32-123">See also</span></span>

- [<span data-ttu-id="41c32-124">C#-publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="41c32-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="41c32-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="41c32-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="41c32-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="41c32-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
