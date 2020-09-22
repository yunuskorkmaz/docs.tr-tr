---
title: Gereken geçici dosya oluşturulamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: c6d8e471796a0fb745289df8b3d1b156265949ca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874664"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="67fe1-102">Gereken geçici dosya oluşturulamıyor</span><span class="sxs-lookup"><span data-stu-id="67fe1-102">Can't create necessary temporary file</span></span>

<span data-ttu-id="67fe1-103">Sürücü, TEMP ortam değişkeni tarafından belirtilen dizini içeren bir tam veya TEMP ortam değişkeni, geçersiz veya salt okunurdur bir sürücü ya da dizin belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="67fe1-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67fe1-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="67fe1-104">To correct this error</span></span>  
  
1. <span data-ttu-id="67fe1-105">Tam ise sürücüdeki dosyaları silin.</span><span class="sxs-lookup"><span data-stu-id="67fe1-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="67fe1-106">GEÇICI ortam değişkeninde farklı bir sürücü belirtin.</span><span class="sxs-lookup"><span data-stu-id="67fe1-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="67fe1-107">GEÇICI ortam değişkeni için geçerli bir sürücü belirtin.</span><span class="sxs-lookup"><span data-stu-id="67fe1-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="67fe1-108">Şu anda belirtilen sürücüden veya dizinden salt okuma kısıtlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="67fe1-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fe1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67fe1-109">See also</span></span>

- [<span data-ttu-id="67fe1-110">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="67fe1-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
