---
title: 'Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 7efdfa09ad7bf58fc3ddc8f702377a4d41b2fed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655393"
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="72335-102">Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="72335-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="72335-103">Visual Basic Derleyicisi bir bildirime sahip bir derleme oluşturmak için Assembly Linker (Al.exe Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="72335-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="72335-104">Bağlayıcı, derleme oluşturma öncesi Emisyonu aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="72335-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="72335-105">Anahtar dosyası veya belirtilen anahtar kapsayıcısında ile ilgili sorun varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="72335-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="72335-106">Bir derlemeyi tam imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72335-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="72335-107">Derlemeyi imzala geciktirmek için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgilerini hakkında bilgi içeren geçerli bir anahtar dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="72335-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="72335-108">Bir derlemeyi gecikmeli imzalanmış olduğunda, özel anahtarı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="72335-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="72335-109">Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="72335-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="72335-110">**Hata Kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="72335-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72335-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="72335-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="72335-112">Tırnak işaretli hata iletisini inceleyin ve konusuna danışın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="72335-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="72335-113">ek açıklama hatası AL1019 ve öneriler</span><span class="sxs-lookup"><span data-stu-id="72335-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="72335-114">Sorun devam ederse, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="72335-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72335-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72335-115">See also</span></span>
- [<span data-ttu-id="72335-116">Nasıl yapılır: Derlemeyi tanımlayıcı bir adla imzalama</span><span class="sxs-lookup"><span data-stu-id="72335-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- <span data-ttu-id="72335-117">[İmzalama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="72335-117">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)
[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
- [<span data-ttu-id="72335-118">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="72335-118">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
