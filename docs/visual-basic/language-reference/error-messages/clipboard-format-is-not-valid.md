---
description: 'Hakkında daha fazla bilgi: Pano biçimi geçerli değil'
title: Pano biçimi geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 58ba6197a14b005cf61d0783e19cb3f957dd2fca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796762"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="d2c97-103">Pano biçimi geçerli değil</span><span class="sxs-lookup"><span data-stu-id="d2c97-103">Clipboard format is not valid</span></span>

<span data-ttu-id="d2c97-104">Belirtilen Pano biçimi yürütülmekte olan yöntemle uyumsuz.</span><span class="sxs-lookup"><span data-stu-id="d2c97-104">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="d2c97-105">Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:</span><span class="sxs-lookup"><span data-stu-id="d2c97-105">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="d2c97-106">`GetText` `SetText` Veya dışında bir pano biçimiyle pano veya yöntemini kullanma `vbCFText` `vbCFLink` .</span><span class="sxs-lookup"><span data-stu-id="d2c97-106">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="d2c97-107">Panonun `GetData` veya `SetData` yönteminin, veya dışında bir pano biçimiyle kullanılması `vbCFBitmap` `vbCFDIB` `vbCFMetafile` .</span><span class="sxs-lookup"><span data-stu-id="d2c97-107">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="d2c97-108">, `GetData` `SetData` `DataObject` Pano biçimi Microsoft Windows 'a kaydedilmediği zaman, kayıtlı BIÇIMLER (&HC000-&hffff) için Microsoft Windows tarafından ayrılmış aralıktaki bir pano biçimiyle veya yöntemlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="d2c97-108">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2c97-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d2c97-109">To correct this error</span></span>  
  
- <span data-ttu-id="d2c97-110">Geçersiz biçimi kaldırın ve geçerli bir tane belirtin.</span><span class="sxs-lookup"><span data-stu-id="d2c97-110">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c97-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c97-111">See also</span></span>

- [<span data-ttu-id="d2c97-112">Pano: diğer biçimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="d2c97-112">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
