---
description: 'Hakkında daha fazla bilgi edinin: BC42033: Hatalı sağlama toplamı değeri, onaltılı olmayan basamaklar veya tek sayıda onaltılık basamak sayısı'
title: Hatalı sağlama toplaması değeri, onaltılık olmayan basamaklar veya tek sayıda onaltılık basamak sayısı
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 051ee0e8ec8b87be4d5feeac8298c0e7a71baea7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103889"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="d16b2-103">BC42033: Hatalı sağlama toplamı değeri, onaltılı olmayan basamaklar veya tek sayıda onaltılık basamak sayısı</span><span class="sxs-lookup"><span data-stu-id="d16b2-103">BC42033: Bad checksum value, non hex digits or odd number of hex digits</span></span>

<span data-ttu-id="d16b2-104">Sağlama toplamı değeri geçersiz onaltılık basamaklar içeriyor veya tek sayıda basamak içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d16b2-104">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>

 <span data-ttu-id="d16b2-105">ASP.NET bir Visual Basic kaynak dosyası (uzantısı. vb) oluşturduğunda, bir sağlama toplamı hesaplar ve tarafından tanımlanan gizli bir kaynak dosyasına koyar `#externalchecksum` .</span><span class="sxs-lookup"><span data-stu-id="d16b2-105">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="d16b2-106">Bu işlemi yapmak için bir. vb dosyası üreten bir kullanıcı da bu işlemi en iyi şekilde dahili kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d16b2-106">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>

 <span data-ttu-id="d16b2-107">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="d16b2-107">By default, this message is a warning.</span></span> <span data-ttu-id="d16b2-108">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d16b2-108">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="d16b2-109">**Hata kimliği:** BC42033</span><span class="sxs-lookup"><span data-stu-id="d16b2-109">**Error ID:** BC42033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d16b2-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d16b2-110">To correct this error</span></span>

1. <span data-ttu-id="d16b2-111">ASP.NET Visual Basic kaynak dosyası üretiyorsa, proje derlemesini yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="d16b2-111">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>

2. <span data-ttu-id="d16b2-112">Yeniden başlatıldıktan sonra bu uyarı devam ederse, ASP.NET 'i yeniden yükleyin ve derlemeyi yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="d16b2-112">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>

3. <span data-ttu-id="d16b2-113">Uyarı hala devam ederse veya ASP.NET kullanmıyorsanız, şartlar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="d16b2-113">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="d16b2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d16b2-114">See also</span></span>

- [<span data-ttu-id="d16b2-115">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="d16b2-115">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="d16b2-116">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d16b2-116">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
