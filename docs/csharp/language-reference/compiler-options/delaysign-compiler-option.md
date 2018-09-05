---
title: -delaysıgn (C# Derleyici Seçenekleri)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518336"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="fa728-102">-delaysıgn (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fa728-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="fa728-103">Bu seçenek, bir dijital imza daha sonra eklenebilir böylece çıkış dosyasına yer ayırmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="fa728-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa728-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa728-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="fa728-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa728-105">Arguments</span></span>

<span data-ttu-id="fa728-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fa728-106">`+` &#124; `-`</span></span>

<span data-ttu-id="fa728-107">Kullanım **- delaysign-** tam imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="fa728-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="fa728-108">Kullanım **- delaysign +** yalnızca derleme içinde ortak anahtar yerleştirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="fa728-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="fa728-109">Varsayılan değer **- delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="fa728-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa728-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa728-110">Remarks</span></span>

<span data-ttu-id="fa728-111">**- Delaysıgn** seçeneği ile birlikte kullanılmadığı sürece hiçbir etkiye sahiptir [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) veya [- keycontaıner](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fa728-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="fa728-112">**- Delaysıgn** ve **- publicsign** seçenekleri karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="fa728-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="fa728-113">Tam imzalı bir derleme istediğinizde; derleyici bildirimi (derleme meta verileri) içeren ve karmayı özel anahtarla imzalar dosyayı karma hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fa728-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="fa728-114">Bu işlem, bir dijital imza bildirimi içeren dosyada depolanan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa728-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="fa728-115">Bir derlemeyi gecikmeli imzalanmış olduğunda, derleyici işlem değil ve daha sonra imzanın eklenmesi için dosyada depolamak imzaya ancak ayırır.</span><span class="sxs-lookup"><span data-stu-id="fa728-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="fa728-116">Örneğin, kullanarak **- delaysign +** derlemeyi genel önbellek üzerine koymasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa728-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="fa728-117">Test edildikten sonra tam olarak derlemeyi kullanarak bir derlemede özel anahtarı yerleştirerek kaydolabilirsiniz [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="fa728-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="fa728-118">Daha fazla bilgi için [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="fa728-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fa728-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fa728-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="fa728-120">Açık **özellikleri** proje sayfası.</span><span class="sxs-lookup"><span data-stu-id="fa728-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="fa728-121">Değiştirme **gecikme yalnızca oturum** özelliği.</span><span class="sxs-lookup"><span data-stu-id="fa728-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="fa728-122">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa728-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa728-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa728-123">See Also</span></span>

- [<span data-ttu-id="fa728-124">C# - publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="fa728-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
- [<span data-ttu-id="fa728-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fa728-125">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="fa728-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="fa728-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
