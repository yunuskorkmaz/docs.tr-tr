---
title: "Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="28914-102">Derleme bildirimi oluşturulurken hata oluştu: &lt;hata iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="28914-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="28914-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici bir derleme bir bildirim oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır.</span><span class="sxs-lookup"><span data-stu-id="28914-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="28914-104">Bağlayıcı derlemesi oluşturma öncesi çıkması aşamasında bir hata bildirdi.</span><span class="sxs-lookup"><span data-stu-id="28914-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="28914-105">Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="28914-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="28914-106">Tam olarak bir derlemeyi imzalamak için ortak ve özel anahtarları hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28914-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="28914-107">Oturum bütünleştirilmiş gecikme için seçmelisiniz **gecikme yalnızca oturum** onay kutusunu işaretleyin ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlayın.</span><span class="sxs-lookup"><span data-stu-id="28914-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="28914-108">Derleme gecikmeli imzalanmış olduğunda özel anahtar gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="28914-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="28914-109">Daha fazla bilgi için bkz: [nasıl yapılır: derleme (Visual Studio) oturum](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="28914-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="28914-110">**Hata Kimliği:** BC30140</span><span class="sxs-lookup"><span data-stu-id="28914-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28914-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="28914-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="28914-112">Tırnak işaretli hata iletisini inceleyin ve konusuna bakın [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) AL1019 hata için daha fazla açıklama ve öneriler</span><span class="sxs-lookup"><span data-stu-id="28914-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="28914-113">Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="28914-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28914-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28914-114">See Also</span></span>  
 [<span data-ttu-id="28914-115">Nasıl yapılır: derleme (Visual Studio) oturum açın</span><span class="sxs-lookup"><span data-stu-id="28914-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="28914-116">İmzalama sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="28914-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="28914-117">Al.exe (derleme bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="28914-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="28914-118">Al.exe aracı hataları ve Uyarıları</span><span class="sxs-lookup"><span data-stu-id="28914-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="28914-119">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="28914-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
