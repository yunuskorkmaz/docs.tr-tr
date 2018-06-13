---
title: -delaysign (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472652"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="c7421-102">-delaysign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c7421-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="c7421-103">Bu seçenek, böylece bir dijital imza daha sonra eklenebilir çıktı dosyasında yer ayırmak için derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7421-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7421-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7421-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="c7421-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7421-105">Arguments</span></span>

<span data-ttu-id="c7421-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c7421-106">`+` &#124; `-`</span></span>

<span data-ttu-id="c7421-107">Kullanım **- delaysign-** tam imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="c7421-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="c7421-108">Kullanım **- delaysign +** yalnızca ortak anahtar derlemede yerleştirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="c7421-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="c7421-109">Varsayılan değer **- delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="c7421-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7421-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7421-110">Remarks</span></span>

<span data-ttu-id="c7421-111">**- Delaysign** seçeneği hiçbir etkisi ile kullanılmadığı sürece [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) veya [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c7421-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="c7421-112">**- Delaysign** ve **- publicsign** seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="c7421-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="c7421-113">Tam imzalı bir derleme istediğinde bildirimi (derleme meta verilerini) içeren ve karmayı özel anahtarıyla imzalar dosyayı derleyici karma hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c7421-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="c7421-114">Bu işlem bildirimini içeren dosyanın depolandığı bir dijital imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7421-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="c7421-115">Bir derlemeyi imzalı gecikme olduğunda derleyici işlem değil ve daha sonra imzanın eklenmesi için imza ancak yer ayırır dosyasında depolamak.</span><span class="sxs-lookup"><span data-stu-id="c7421-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="c7421-116">Örneğin, kullanarak **- delaysign +** genel önbelleğinde derleme yerleştirilecek tester sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7421-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="c7421-117">Sınama sonra tam olarak derleme özel anahtarı kullanarak derlemeye koyarak oturum [derleme bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="c7421-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="c7421-118">Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="c7421-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c7421-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c7421-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="c7421-120">Açık **özellikleri** projesi için sayfa.</span><span class="sxs-lookup"><span data-stu-id="c7421-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="c7421-121">Değiştirme **gecikme yalnızca oturum** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7421-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="c7421-122">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7421-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7421-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7421-123">See Also</span></span>

 [<span data-ttu-id="c7421-124">C# - publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="c7421-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
 [<span data-ttu-id="c7421-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c7421-125">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="c7421-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c7421-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
