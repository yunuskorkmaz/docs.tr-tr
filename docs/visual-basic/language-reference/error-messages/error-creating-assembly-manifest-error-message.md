---
title: "Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="df6ee-102">Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="df6ee-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="df6ee-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici bir derleme bir bildirim oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="df6ee-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="df6ee-104">Bağlayıcı derlemesi oluşturma öncesi çıkması aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="df6ee-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="df6ee-105">Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="df6ee-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="df6ee-106">Tam olarak bir derlemeyi imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df6ee-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="df6ee-107">Oturum bütünleştirilmiş gecikme için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlayın.</span><span class="sxs-lookup"><span data-stu-id="df6ee-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="df6ee-108">Derleme gecikmeli imzalanmış olduğunda özel anahtar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="df6ee-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="df6ee-109">Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="df6ee-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="df6ee-110">**Hata Kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="df6ee-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="df6ee-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="df6ee-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="df6ee-112">Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="df6ee-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="df6ee-113">hata AL1019 daha ayrıntılı bir açıklama ve öneriler</span><span class="sxs-lookup"><span data-stu-id="df6ee-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="df6ee-114">Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="df6ee-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6ee-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df6ee-115">See Also</span></span>  
 [<span data-ttu-id="df6ee-116">Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama</span><span class="sxs-lookup"><span data-stu-id="df6ee-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="df6ee-117">İmzalama Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="df6ee-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="df6ee-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="df6ee-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="df6ee-119">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="df6ee-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
