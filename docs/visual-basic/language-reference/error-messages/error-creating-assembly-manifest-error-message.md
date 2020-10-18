---
title: 'Derleme bildirimi oluşturulurken hata oldu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: a772167966c4ec858197cc2032f4ae3d4e86070c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163421"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a><span data-ttu-id="689ca-102">BC30140: derleme bildirimi oluşturulurken hata oluştu: \<error message></span><span class="sxs-lookup"><span data-stu-id="689ca-102">BC30140: Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="689ca-103">Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="689ca-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="689ca-104">Bağlayıcı, derlemeyi oluşturmak için önceden egörev aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="689ca-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>

 <span data-ttu-id="689ca-105">Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="689ca-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="689ca-106">Bir derlemeyi tamamen imzalamak için ortak ve özel anahtarlarla ilgili bilgileri içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="689ca-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="689ca-107">Bir derlemeyi imzalamayı geciktirmek için **yalnızca gecikmeli imzala** onay kutusunu seçmeniz ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="689ca-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="689ca-108">Bir derleme Gecikmeli imzalanmışsa özel anahtar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="689ca-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="689ca-109">Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="689ca-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

 <span data-ttu-id="689ca-110">**Hata kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="689ca-110">**Error ID:** BC30140</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="689ca-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="689ca-111">To correct this error</span></span>

1. <span data-ttu-id="689ca-112">Alıntı yapılan hata iletisini inceleyin ve [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="689ca-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="689ca-113">hata AL1019 daha fazla açıklama ve öneri</span><span class="sxs-lookup"><span data-stu-id="689ca-113">for error AL1019 further explanation and advice</span></span>

2. <span data-ttu-id="689ca-114">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="689ca-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="689ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="689ca-115">See also</span></span>

- [<span data-ttu-id="689ca-116">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="689ca-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="689ca-117">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="689ca-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="689ca-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="689ca-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="689ca-119">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="689ca-119">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
