---
title: Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 5c01e918e1f607febc10be89c3d27c50870c401a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589257"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="a2eeb-102">Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı</span><span class="sxs-lookup"><span data-stu-id="a2eeb-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="a2eeb-103">Bir sağlama toplamı değeri geçersiz onaltılık basamak içeriyor veya tek bir basamak sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="a2eeb-104">ASP.NET bir Visual Basic kaynak dosyası (uzantısı .vb) oluşturduğunda, bir sağlama toplamı hesaplar ve tarafından tanımlanan gizli kaynak dosyaya yerleştirir `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="a2eeb-105">Ayrıca bunun .vb dosyası oluşturma bir kullanıcı için mümkündür, ancak iç kullanım için en iyi sol bu işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="a2eeb-106">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-106">By default, this message is a warning.</span></span> <span data-ttu-id="a2eeb-107">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a2eeb-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a2eeb-108">**Hata Kimliği:** BC42033</span><span class="sxs-lookup"><span data-stu-id="a2eeb-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2eeb-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a2eeb-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="a2eeb-110">Proje derleme ASP.NET Visual Basic kaynak dosyası oluşturma, yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="a2eeb-111">Bu uyarıyı yeniden başlatıldıktan sonra devam ederse, ASP.NET yeniden yükleyin ve yapı yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="a2eeb-112">Uyarı devam ederse veya ASP.NET kullanmıyorsanız, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2eeb-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2eeb-113">See Also</span></span>  
 [<span data-ttu-id="a2eeb-114">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="a2eeb-114">ASP.NET Overview</span></span>](https://msdn.microsoft.com/library/4w3ex9c2.aspx)  
 [<span data-ttu-id="a2eeb-115">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="a2eeb-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
