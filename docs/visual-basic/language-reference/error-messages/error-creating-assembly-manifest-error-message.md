---
title: 'Derleme bildirimi oluşturulurken hata oluştu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 0f67b772bab3104c00510954d01b200aadfa9e8a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296296"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="31362-102">Derleme bildirimi oluşturulurken hata oluştu: \<hata iletisi ></span><span class="sxs-lookup"><span data-stu-id="31362-102">Error creating assembly manifest: \<error message></span></span>
<span data-ttu-id="31362-103">Visual Basic Derleyicisi bir bildirime sahip bir derleme oluşturmak için Assembly Linker (Al.exe Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="31362-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="31362-104">Bağlayıcı, derleme oluşturma öncesi Emisyonu aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="31362-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="31362-105">Anahtar dosyası veya belirtilen anahtar kapsayıcısında ile ilgili sorun varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="31362-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="31362-106">Bir derlemeyi tam imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31362-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="31362-107">Derlemeyi imzala geciktirmek için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgilerini hakkında bilgi içeren geçerli bir anahtar dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="31362-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="31362-108">Bir derlemeyi gecikmeli imzalanmış olduğunda, özel anahtarı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="31362-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="31362-109">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="31362-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="31362-110">**Hata Kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="31362-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31362-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="31362-111">To correct this error</span></span>  
  
1. <span data-ttu-id="31362-112">Tırnak işaretli hata iletisini inceleyin ve konusuna danışın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="31362-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="31362-113">ek açıklama hatası AL1019 ve öneriler</span><span class="sxs-lookup"><span data-stu-id="31362-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="31362-114">Sorun devam ederse, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="31362-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31362-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31362-115">See also</span></span>

- [<span data-ttu-id="31362-116">Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="31362-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="31362-117">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="31362-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="31362-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="31362-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="31362-119">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="31362-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
