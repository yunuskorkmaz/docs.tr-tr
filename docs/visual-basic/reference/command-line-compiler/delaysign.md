---
description: Daha fazla bilgi edinin:-delaysign
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: fc3e52f63431da870355e369e6ffeb8b7b14c5ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461508"
---
# <a name="-delaysign"></a><span data-ttu-id="48975-103">-delaysign</span><span class="sxs-lookup"><span data-stu-id="48975-103">-delaysign</span></span>

<span data-ttu-id="48975-104">Derlemenin tamamen veya kısmen imzalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="48975-104">Specifies whether the assembly will be fully or partially signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="48975-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="48975-105">Syntax</span></span>

```console
-delaysign[+ | -]
```

## <a name="arguments"></a><span data-ttu-id="48975-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="48975-106">Arguments</span></span>

<span data-ttu-id="48975-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="48975-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="48975-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="48975-108">Optional.</span></span> <span data-ttu-id="48975-109">`-delaysign-`Tam olarak imzalanan bir derleme istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="48975-109">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="48975-110">`-delaysign+`Ortak anahtarı derlemeye yerleştirmek ve imzalı karma için alan ayırmak istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="48975-110">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="48975-111">Varsayılan değer: `-delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="48975-111">The default is `-delaysign-`.</span></span>

## <a name="remarks"></a><span data-ttu-id="48975-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48975-112">Remarks</span></span>

<span data-ttu-id="48975-113">`-delaysign` [-Keyfile](keyfile.md) veya [-keycontainer](keycontainer.md)ile kullanılmamışsa seçeneğinin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="48975-113">The `-delaysign` option has no effect unless used with [-keyfile](keyfile.md) or [-keycontainer](keycontainer.md).</span></span>

<span data-ttu-id="48975-114">Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="48975-114">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="48975-115">Elde edilen dijital imza, bildirimi içeren dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="48975-115">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="48975-116">Bir derlemenin gecikmesi gecikmeli olduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imza daha sonra eklenebilmesi için dosyada yer ayırır.</span><span class="sxs-lookup"><span data-stu-id="48975-116">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="48975-117">Örneğin, kullanarak `-delaysign+` bir kuruluştaki geliştirici, test edicinin genel derleme önbelleği ile kaydedebilmesi ve kullanması için imzasız test sürümlerini dağıtabilir.</span><span class="sxs-lookup"><span data-stu-id="48975-117">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="48975-118">Derlemedeki iş tamamlandığında, kuruluşun özel anahtarından sorumlu olan kişi derlemeyi tamamen imzalayabilir.</span><span class="sxs-lookup"><span data-stu-id="48975-118">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="48975-119">Bu compartmen, kuruluşun özel anahtarının açıklanmasını koruurken tüm geliştiricilerin derlemeler üzerinde çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="48975-119">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>

<span data-ttu-id="48975-120">Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="48975-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="48975-121">Visual Studio tümleşik geliştirme ortamında Set-delaysign</span><span class="sxs-lookup"><span data-stu-id="48975-121">To set -delaysign in the Visual Studio integrated development environment</span></span>

1. <span data-ttu-id="48975-122">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48975-122">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="48975-123">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="48975-123">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="48975-124">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="48975-124">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="48975-125">Değeri **yalnızca gecikmeli imzala** kutusunda ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48975-125">Set the value in the **Delay sign only** box.</span></span>

## <a name="see-also"></a><span data-ttu-id="48975-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48975-126">See also</span></span>

- [<span data-ttu-id="48975-127">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="48975-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="48975-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="48975-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="48975-129">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="48975-129">-keycontainer</span></span>](keycontainer.md)
- [<span data-ttu-id="48975-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="48975-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
