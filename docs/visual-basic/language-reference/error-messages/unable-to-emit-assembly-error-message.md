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
ms.openlocfilehash: 015ab6e1d186495d72bddd65678ab15088c0f1b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674889"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="03b39-103">BC30145: bütünleştirilmiş kod yayılamıyor: \<error message></span><span class="sxs-lookup"><span data-stu-id="03b39-103">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="03b39-104">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (*Al.exe* ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="03b39-104">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="03b39-105">**Hata kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="03b39-105">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="03b39-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="03b39-106">To correct this error</span></span>

1. <span data-ttu-id="03b39-107">Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="03b39-107">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="03b39-108">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ya da [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="03b39-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="03b39-109">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="03b39-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="03b39-110">Derlemeyi el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="03b39-110">To sign the assembly manually</span></span>

1. <span data-ttu-id="03b39-111">Ortak/özel anahtar çifti dosyası oluşturmak için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) kullanın.</span><span class="sxs-lookup"><span data-stu-id="03b39-111">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="03b39-112">Bu dosya *. snk* uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="03b39-112">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="03b39-113">Projenizden hatayı üreten COM başvurusunu silin.</span><span class="sxs-lookup"><span data-stu-id="03b39-113">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="03b39-114">[Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md)açın.</span><span class="sxs-lookup"><span data-stu-id="03b39-114">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="03b39-115">Windows 10 ' da, görev çubuğundaki arama kutusuna **Geliştirici komut istemi** ' ni girin.</span><span class="sxs-lookup"><span data-stu-id="03b39-115">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="03b39-116">Ardından, sonuçlar listesinden **VS 2017 için geliştirici komut istemi** seçin.</span><span class="sxs-lookup"><span data-stu-id="03b39-116">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="03b39-117">Dizinini, derleme sarmalayıcıyı yerleştirmek istediğiniz dizine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="03b39-117">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="03b39-118">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="03b39-118">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="03b39-119">Girebileceğiniz gerçek komuta bir örnek:</span><span class="sxs-lookup"><span data-stu-id="03b39-119">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="03b39-120">Bir yol veya dosya boşluk içeriyorsa çift tırnak işareti kullanın.</span><span class="sxs-lookup"><span data-stu-id="03b39-120">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="03b39-121">Visual Studio 'da, yeni oluşturduğunuz dosyaya bir .NET derleme başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03b39-121">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="03b39-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03b39-122">See also</span></span>

- [<span data-ttu-id="03b39-123">Al.exe</span><span class="sxs-lookup"><span data-stu-id="03b39-123">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="03b39-124">Sn.exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="03b39-124">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="03b39-125">Nasıl yapılır: Public-Private anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="03b39-125">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="03b39-126">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="03b39-126">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
