---
description: 'Şu konuda daha fazla bilgi edinin: BC30140: derleme bildirimi oluşturma hatası: <error message>'
title: 'Derleme bildirimi oluşturulurken hata oldu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e2c690ab198e11a70a2fc3bba925ccc4ccb31c79
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103419"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a><span data-ttu-id="2a82e-103">BC30140: derleme bildirimi oluşturulurken hata oluştu: \<error message></span><span class="sxs-lookup"><span data-stu-id="2a82e-103">BC30140: Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="2a82e-104">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="2a82e-104">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="2a82e-105">Bağlayıcı, derlemeyi oluşturmak için önceden egörev aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="2a82e-105">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>

 <span data-ttu-id="2a82e-106">Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2a82e-106">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="2a82e-107">Bir derlemeyi tamamen imzalamak için ortak ve özel anahtarlarla ilgili bilgileri içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a82e-107">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="2a82e-108">Bir derlemeyi imzalamayı geciktirmek için **yalnızca gecikmeli imzala** onay kutusunu seçmeniz ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a82e-108">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="2a82e-109">Bir derleme Gecikmeli imzalanmışsa özel anahtar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2a82e-109">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="2a82e-110">Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="2a82e-110">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

 <span data-ttu-id="2a82e-111">**Hata kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="2a82e-111">**Error ID:** BC30140</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2a82e-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2a82e-112">To correct this error</span></span>

1. <span data-ttu-id="2a82e-113">Alıntı yapılan hata iletisini inceleyin ve [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="2a82e-113">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="2a82e-114">hata AL1019 daha fazla açıklama ve öneri</span><span class="sxs-lookup"><span data-stu-id="2a82e-114">for error AL1019 further explanation and advice</span></span>

2. <span data-ttu-id="2a82e-115">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="2a82e-115">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a82e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a82e-116">See also</span></span>

- [<span data-ttu-id="2a82e-117">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="2a82e-117">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="2a82e-118">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="2a82e-118">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="2a82e-119">Al.exe</span><span class="sxs-lookup"><span data-stu-id="2a82e-119">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="2a82e-120">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2a82e-120">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
