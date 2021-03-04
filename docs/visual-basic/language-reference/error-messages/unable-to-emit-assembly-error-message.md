---
description: 'Şu konuda daha fazla bilgi edinin: BC30145: bütünleştirilmiş kod yayılamıyor: <error message>'
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 393571f5b1fab518f379bbd6f4e6f1cb62a74b26
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104789"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="44e74-103">BC30145: bütünleştirilmiş kod yayılamıyor: \<error message></span><span class="sxs-lookup"><span data-stu-id="44e74-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="44e74-104">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (*Al.exe* ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="44e74-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="44e74-105">**Hata kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="44e74-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="44e74-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="44e74-106">To correct this error</span></span>

1. <span data-ttu-id="44e74-107">Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="44e74-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="44e74-108">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ya da [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="44e74-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="44e74-109">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="44e74-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="44e74-110">Derlemeyi el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="44e74-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="44e74-111">Ortak/özel anahtar çifti dosyası oluşturmak için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="44e74-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="44e74-112">Bu dosya *. snk* uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44e74-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="44e74-113">Projenizden hatayı üreten COM başvurusunu silin.</span><span class="sxs-lookup"><span data-stu-id="44e74-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="44e74-114">[Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md)açın.</span><span class="sxs-lookup"><span data-stu-id="44e74-114">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

4. <span data-ttu-id="44e74-115">Dizinini, derleme sarmalayıcıyı yerleştirmek istediğiniz dizine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="44e74-115">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="44e74-116">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="44e74-116">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="44e74-117">Girebileceğiniz gerçek komuta bir örnek:</span><span class="sxs-lookup"><span data-stu-id="44e74-117">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="44e74-118">Bir yol veya dosya boşluk içeriyorsa çift tırnak işareti kullanın.</span><span class="sxs-lookup"><span data-stu-id="44e74-118">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="44e74-119">Visual Studio 'da, yeni oluşturduğunuz dosyaya bir .NET derleme başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44e74-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="44e74-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44e74-120">See also</span></span>

- [<span data-ttu-id="44e74-121">Al.exe</span><span class="sxs-lookup"><span data-stu-id="44e74-121">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="44e74-122">Sn.exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="44e74-122">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="44e74-123">Nasıl yapılır: Public-Private anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="44e74-123">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="44e74-124">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="44e74-124">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
