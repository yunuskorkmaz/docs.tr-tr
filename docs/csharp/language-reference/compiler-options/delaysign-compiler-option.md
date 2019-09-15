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
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970439"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="20057-102">-delaysign (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="20057-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="20057-103">Bu seçenek derleyicinin çıkış dosyasında alan ayırmasını sağlayarak bir dijital imzanın daha sonra eklenebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="20057-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="20057-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20057-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="20057-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="20057-105">Arguments</span></span>

<span data-ttu-id="20057-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="20057-106">`+` &#124; `-`</span></span>

<span data-ttu-id="20057-107">Tam olarak imzalanan bir derlemeyi istiyorsanız **-delaysign-** kullanın.</span><span class="sxs-lookup"><span data-stu-id="20057-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="20057-108">Yalnızca ortak anahtarı derlemeye yerleştirmek istiyorsanız **-delaysign +** kullanın.</span><span class="sxs-lookup"><span data-stu-id="20057-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="20057-109">Varsayılan değer **-delaysign-** .</span><span class="sxs-lookup"><span data-stu-id="20057-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="20057-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20057-110">Remarks</span></span>

<span data-ttu-id="20057-111">\- [Keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmamışsa **-delaysign** seçeneğinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="20057-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="20057-112">**-Delaysign** ve **-publicsign** seçenekleri birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="20057-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="20057-113">Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="20057-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="20057-114">Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20057-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="20057-115">Bir derlemenin gecikmesi gecikmeli kaydolduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenebilmesi için dosyada alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="20057-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="20057-116">Örneğin, **-delaysign +** kullanılması, bir sınayıcı 'ın derlemeyi genel önbellekte almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="20057-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="20057-117">Test ettikten sonra, derleme [bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tamamen imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20057-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="20057-118">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="20057-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="20057-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="20057-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="20057-120">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="20057-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="20057-121">**Yalnızca gecikmeli imzala** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20057-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="20057-122">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="20057-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="20057-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20057-123">See also</span></span>

- [<span data-ttu-id="20057-124">C#-publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="20057-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="20057-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="20057-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="20057-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="20057-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
