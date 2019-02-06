---
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: d564f4f4462a691504297d65575956c5f06691ca
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759229"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="14fdc-102">Derleme yayılamıyor: \<hata iletisi ></span><span class="sxs-lookup"><span data-stu-id="14fdc-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="14fdc-103">Visual Basic Derleyicisi Assembly Linker çağırır (*Al.exe*Alink olarak da bilinen) bir bildirim ve bağlayıcı sahip bir derleme oluşturmak için derleme oluşturma Emisyonu aşamasında bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="14fdc-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="14fdc-104">**Hata Kimliği:** BC30145</span><span class="sxs-lookup"><span data-stu-id="14fdc-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="14fdc-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="14fdc-105">To correct this error</span></span>

1. <span data-ttu-id="14fdc-106">Tırnak işaretli hata iletisini inceleyin ve konusuna danışın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) daha ayrıntılı bir açıklama ve öneriler için.</span><span class="sxs-lookup"><span data-stu-id="14fdc-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="14fdc-107">Derlemeyi kullanarak el ile açmayı deneyin [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="14fdc-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="14fdc-108">Sorun devam ederse, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="14fdc-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="14fdc-109">Derlemeyi el ile imzalamak için</span><span class="sxs-lookup"><span data-stu-id="14fdc-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="14fdc-110">Kullanma [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) bir ortak/özel anahtar çifti dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14fdc-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="14fdc-111">Bu dosyanın bir *.snk* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="14fdc-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="14fdc-112">Projenizden hata oluşturuyor COM başvurusu silin.</span><span class="sxs-lookup"><span data-stu-id="14fdc-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="14fdc-113">Açık [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="14fdc-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="14fdc-114">Windows 10, girin **Geliştirici komut istemi** görev çubuğundaki arama kutusuna.</span><span class="sxs-lookup"><span data-stu-id="14fdc-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="14fdc-115">Ardından, **VS 2017 için geliştirici komut istemi** sonuçları listesinde.</span><span class="sxs-lookup"><span data-stu-id="14fdc-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="14fdc-116">Dizini, derleme sarmalayıcısı yerleştirmek istediğiniz dizine geçin.</span><span class="sxs-lookup"><span data-stu-id="14fdc-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="14fdc-117">Aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="14fdc-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="14fdc-118">Şunu yazabilirsiniz gerçek komut bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="14fdc-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="14fdc-119">Bir yol veya dosya boşluk içeriyorsa çift tırnak işaretleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="14fdc-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="14fdc-120">Visual Studio'da oluşturduğunuz dosya bir .NET derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14fdc-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="14fdc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14fdc-121">See also</span></span>

- [<span data-ttu-id="14fdc-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="14fdc-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="14fdc-123">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="14fdc-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="14fdc-124">Nasıl yapılır: Genel-özel anahtar çifti oluşturma</span><span class="sxs-lookup"><span data-stu-id="14fdc-124">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="14fdc-125">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="14fdc-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)