---
title: Pano biçimi geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874592"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="bb5c4-102">Pano biçimi geçerli değil</span><span class="sxs-lookup"><span data-stu-id="bb5c4-102">Clipboard format is not valid</span></span>

<span data-ttu-id="bb5c4-103">Belirtilen Pano biçimi yürütülmekte olan yöntemle uyumsuz.</span><span class="sxs-lookup"><span data-stu-id="bb5c4-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="bb5c4-104">Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:</span><span class="sxs-lookup"><span data-stu-id="bb5c4-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="bb5c4-105">`GetText` `SetText` Veya dışında bir pano biçimiyle pano veya yöntemini kullanma `vbCFText` `vbCFLink` .</span><span class="sxs-lookup"><span data-stu-id="bb5c4-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="bb5c4-106">Panonun `GetData` veya `SetData` yönteminin, veya dışında bir pano biçimiyle kullanılması `vbCFBitmap` `vbCFDIB` `vbCFMetafile` .</span><span class="sxs-lookup"><span data-stu-id="bb5c4-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="bb5c4-107">, `GetData` `SetData` `DataObject` Pano biçimi Microsoft Windows 'a kaydedilmediği zaman, kayıtlı BIÇIMLER (&HC000-&hffff) için Microsoft Windows tarafından ayrılmış aralıktaki bir pano biçimiyle veya yöntemlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="bb5c4-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb5c4-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bb5c4-108">To correct this error</span></span>  
  
- <span data-ttu-id="bb5c4-109">Geçersiz biçimi kaldırın ve geçerli bir tane belirtin.</span><span class="sxs-lookup"><span data-stu-id="bb5c4-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5c4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb5c4-110">See also</span></span>

- [<span data-ttu-id="bb5c4-111">Pano: diğer biçimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="bb5c4-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
