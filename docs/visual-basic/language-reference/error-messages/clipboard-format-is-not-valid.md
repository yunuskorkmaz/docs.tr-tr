---
title: Pano biçimi geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586227"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="c8a7e-102">Pano biçimi geçerli değil</span><span class="sxs-lookup"><span data-stu-id="c8a7e-102">Clipboard format is not valid</span></span>
<span data-ttu-id="c8a7e-103">Belirtilen Pano biçimi yürütülmekte yöntemi ile uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="c8a7e-104">Bu hatanın olası nedenleri arasında aşağıdakiler vardır:</span><span class="sxs-lookup"><span data-stu-id="c8a7e-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="c8a7e-105">Pano kullanarak `GetText` veya `SetText` dışında bir pano biçimi yöntemiyle `vbCFText` veya `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="c8a7e-106">Pano kullanarak `GetData` veya `SetData` dışında bir pano biçimi yöntemiyle `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="c8a7e-107">Kullanarak `DataObject``GetData` yöntemi veya `SetData` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılan aralıkla Pano biçiminde yöntemiyle ne zaman bu pano biçimi kaydettirilemedi Microsoft Windows ile.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8a7e-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c8a7e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c8a7e-109">Geçersiz biçim kaldırın ve geçerli bir tane belirtin.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a7e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a7e-110">See Also</span></span>  
 [<span data-ttu-id="c8a7e-111">Pano: Diğer Biçimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="c8a7e-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
