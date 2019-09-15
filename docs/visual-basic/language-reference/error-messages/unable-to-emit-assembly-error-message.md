---
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968860"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="06ca7-102">Bütünleştirilmiş kod yayılamıyor: \<hata iletisi ></span><span class="sxs-lookup"><span data-stu-id="06ca7-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="06ca7-103">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme Bağlayıcısı (*al. exe*, ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="06ca7-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="06ca7-104">**Hata KIMLIĞI:** BC30145</span><span class="sxs-lookup"><span data-stu-id="06ca7-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="06ca7-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="06ca7-105">To correct this error</span></span>

1. <span data-ttu-id="06ca7-106">Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [al. exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="06ca7-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="06ca7-107">[Al. exe](../../../framework/tools/al-exe-assembly-linker.md) veya [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="06ca7-108">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="06ca7-109">Derlemeyi el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="06ca7-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="06ca7-110">Bir ortak/özel anahtar çifti dosyası oluşturmak için [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="06ca7-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="06ca7-111">Bu dosya *. snk* uzantısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="06ca7-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="06ca7-112">Projenizden hatayı üreten COM başvurusunu silin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="06ca7-113">[Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md)açın.</span><span class="sxs-lookup"><span data-stu-id="06ca7-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="06ca7-114">Windows 10 ' da, görev çubuğundaki arama kutusuna **Geliştirici komut istemi** ' ni girin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="06ca7-115">Ardından, sonuçlar listesinden **VS 2017 için geliştirici komut istemi** seçin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="06ca7-116">Dizinini, derleme sarmalayıcıyı yerleştirmek istediğiniz dizine değiştirin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="06ca7-117">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="06ca7-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="06ca7-118">Girebileceğiniz gerçek komuta bir örnek:</span><span class="sxs-lookup"><span data-stu-id="06ca7-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="06ca7-119">Bir yol veya dosya boşluk içeriyorsa çift tırnak işareti kullanın.</span><span class="sxs-lookup"><span data-stu-id="06ca7-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="06ca7-120">Visual Studio 'da, yeni oluşturduğunuz dosyaya bir .NET derleme başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06ca7-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="06ca7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06ca7-121">See also</span></span>

- [<span data-ttu-id="06ca7-122">Al. exe</span><span class="sxs-lookup"><span data-stu-id="06ca7-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="06ca7-123">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="06ca7-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="06ca7-124">Nasıl yapılır: Ortak özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="06ca7-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="06ca7-125">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="06ca7-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
