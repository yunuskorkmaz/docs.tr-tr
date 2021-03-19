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
ms.openlocfilehash: 2ba476b39b6aa441d8778ee0618dcc3dcf3f7ac8
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653289"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="f36d5-103">BC30145: bütünleştirilmiş kod yayılamıyor: \<error message></span><span class="sxs-lookup"><span data-stu-id="f36d5-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="f36d5-104">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (*Al.exe* ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="f36d5-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="f36d5-105">**Hata kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="f36d5-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f36d5-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f36d5-106">To correct this error</span></span>

1. <span data-ttu-id="f36d5-107">Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="f36d5-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="f36d5-108">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ya da [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="f36d5-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="f36d5-109">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="f36d5-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="f36d5-110">Derlemeyi el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="f36d5-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="f36d5-111">Ortak/özel anahtar çifti dosyası oluşturmak için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f36d5-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="f36d5-112">Bu dosya *. snk* uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f36d5-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="f36d5-113">Projenizden hatayı üreten COM başvurusunu silin.</span><span class="sxs-lookup"><span data-stu-id="f36d5-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="f36d5-114">[Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)'i açın.</span><span class="sxs-lookup"><span data-stu-id="f36d5-114">Open [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

4. <span data-ttu-id="f36d5-115">Dizinini, derleme sarmalayıcıyı yerleştirmek istediğiniz dizine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f36d5-115">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="f36d5-116">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="f36d5-116">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="f36d5-117">Girebileceğiniz gerçek komuta bir örnek:</span><span class="sxs-lookup"><span data-stu-id="f36d5-117">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="f36d5-118">Bir yol veya dosya boşluk içeriyorsa çift tırnak işareti kullanın.</span><span class="sxs-lookup"><span data-stu-id="f36d5-118">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="f36d5-119">Visual Studio 'da, yeni oluşturduğunuz dosyaya bir .NET derleme başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f36d5-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="f36d5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f36d5-120">See also</span></span>

- [<span data-ttu-id="f36d5-121">Al.exe</span><span class="sxs-lookup"><span data-stu-id="f36d5-121">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="f36d5-122">Sn.exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="f36d5-122">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="f36d5-123">Nasıl yapılır: Public-Private anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="f36d5-123">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="f36d5-124">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f36d5-124">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
