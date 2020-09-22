---
title: Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 612f0b273bacab541e2d634612a104eff1f4a796
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875159"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="af7cc-102">Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı</span><span class="sxs-lookup"><span data-stu-id="af7cc-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>

<span data-ttu-id="af7cc-103">Sağlama toplamı değeri geçersiz onaltılık basamaklar içeriyor veya tek sayıda basamak içeriyor.</span><span class="sxs-lookup"><span data-stu-id="af7cc-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="af7cc-104">ASP.NET bir Visual Basic kaynak dosyası (uzantısı. vb) oluşturduğunda, bir sağlama toplamı hesaplar ve tarafından tanımlanan gizli bir kaynak dosyasına koyar `#externalchecksum` .</span><span class="sxs-lookup"><span data-stu-id="af7cc-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="af7cc-105">Bu işlemi yapmak için bir. vb dosyası üreten bir kullanıcı da bu işlemi en iyi şekilde dahili kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="af7cc-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="af7cc-106">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="af7cc-106">By default, this message is a warning.</span></span> <span data-ttu-id="af7cc-107">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="af7cc-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="af7cc-108">**Hata kimliği:** BC42033</span><span class="sxs-lookup"><span data-stu-id="af7cc-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af7cc-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="af7cc-109">To correct this error</span></span>  
  
1. <span data-ttu-id="af7cc-110">ASP.NET Visual Basic kaynak dosyası üretiyorsa, proje derlemesini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="af7cc-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2. <span data-ttu-id="af7cc-111">Yeniden başlatıldıktan sonra bu uyarı devam ederse, ASP.NET 'i yeniden yükleyin ve derlemeyi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="af7cc-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3. <span data-ttu-id="af7cc-112">Uyarı hala devam ederse veya ASP.NET kullanmıyorsanız, şartlar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="af7cc-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7cc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af7cc-113">See also</span></span>

- [<span data-ttu-id="af7cc-114">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="af7cc-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="af7cc-115">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="af7cc-115">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
