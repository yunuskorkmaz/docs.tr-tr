---
title: Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 81156fd7b1c9957486bcdd898c90a2bad2945829
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340314"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="367d5-102">Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı</span><span class="sxs-lookup"><span data-stu-id="367d5-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="367d5-103">Bir sağlama toplamı değeri geçersiz onaltılık basamaklar içermeyen veya tek sayıda basamak içeriyor.</span><span class="sxs-lookup"><span data-stu-id="367d5-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="367d5-104">ASP.NET bir Visual Basic kaynak dosyası (.vb uzantısı) oluşturduğunda, bir sağlama toplamı hesaplar ve bir gizli kaynak dosyası tarafından tanımlanan yerleştirir `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="367d5-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="367d5-105">Ayrıca bunu yapmanın .vb dosyası oluşturma bir kullanıcı için mümkündür ancak bu işlem, iç kullanım için en iyi sol.</span><span class="sxs-lookup"><span data-stu-id="367d5-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="367d5-106">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="367d5-106">By default, this message is a warning.</span></span> <span data-ttu-id="367d5-107">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="367d5-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="367d5-108">**Hata Kimliği:** BC42033</span><span class="sxs-lookup"><span data-stu-id="367d5-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="367d5-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="367d5-109">To correct this error</span></span>  
  
1. <span data-ttu-id="367d5-110">Visual Basic kaynak dosyası ASP.NET oluşturuyorsa, proje derlemesi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="367d5-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2. <span data-ttu-id="367d5-111">Bu uyarıyı yeniden başlatıldıktan sonra devam ederse, ASP.NET yeniden yükleyin ve derlemeyi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="367d5-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3. <span data-ttu-id="367d5-112">Uyarı devam ederse ya da bu ASP.NET kullanmıyorsanız, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="367d5-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367d5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="367d5-113">See also</span></span>

- [<span data-ttu-id="367d5-114">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="367d5-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="367d5-115">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="367d5-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
