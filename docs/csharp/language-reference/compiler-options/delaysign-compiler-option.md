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
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970439"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="b5f39-102">-delaysign (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b5f39-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="b5f39-103">Bu seçenek, derleyicinin çıktı dosyasında yer ayırmasına neden olur, böylece dijital imza daha sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b5f39-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5f39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5f39-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="b5f39-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b5f39-105">Arguments</span></span>

<span data-ttu-id="b5f39-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="b5f39-106">`+` &#124; `-`</span></span>

<span data-ttu-id="b5f39-107">Tam imzalı bir montaj istiyorsanız **-delaysign-** kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5f39-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="b5f39-108">Ortak anahtarı yalnızca derlemeye yerleştirmek istiyorsanız **-delaysign+** kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5f39-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="b5f39-109">Varsayılan **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="b5f39-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5f39-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5f39-110">Remarks</span></span>

<span data-ttu-id="b5f39-111">**-delaysign** seçeneği [-keyfile](./keyfile-compiler-option.md) veya [-keycontainer](./keycontainer-compiler-option.md)ile kullanılmadığı sürece hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5f39-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="b5f39-112">**-delaysign** **ve-publicsign** seçenekleri birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="b5f39-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="b5f39-113">Tam olarak imzalanmış bir derleme istediğinizde, derleyici, manifesto (derleme meta verileri) içeren dosyayı ve özel anahtarla karma işaretleri içeren dosyayı haşlar.</span><span class="sxs-lookup"><span data-stu-id="b5f39-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="b5f39-114">Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b5f39-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="b5f39-115">Bir derleme geciktiğinde, derleyici imzayı hesaplamaz ve depolamaz, ancak imzanın daha sonra eklenabilmesi için dosyada yer ayırır.</span><span class="sxs-lookup"><span data-stu-id="b5f39-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="b5f39-116">Örneğin, **-delaysign+** kullanmak, bir testedenin derlemeyi genel önbelleğe koymasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b5f39-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="b5f39-117">Test ten sonra, [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tam olarak imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5f39-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="b5f39-118">Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)</span><span class="sxs-lookup"><span data-stu-id="b5f39-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b5f39-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b5f39-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b5f39-120">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="b5f39-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="b5f39-121">Yalnızca **Gecikme işareti** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b5f39-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="b5f39-122">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A></span><span class="sxs-lookup"><span data-stu-id="b5f39-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f39-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f39-123">See also</span></span>

- [<span data-ttu-id="b5f39-124">C# -publicsign seçeneği</span><span class="sxs-lookup"><span data-stu-id="b5f39-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="b5f39-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b5f39-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b5f39-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b5f39-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
