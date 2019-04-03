---
title: Pano biçimi geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817186"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="a7a0a-102">Pano biçimi geçerli değil</span><span class="sxs-lookup"><span data-stu-id="a7a0a-102">Clipboard format is not valid</span></span>
<span data-ttu-id="a7a0a-103">Belirtilen Pano biçimi yürütülen yöntemi ile uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="a7a0a-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="a7a0a-104">Bu hata için olası nedenler arasındadır:</span><span class="sxs-lookup"><span data-stu-id="a7a0a-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="a7a0a-105">Pano kullanarak `GetText` veya `SetText` yöntemi ile bir pano biçimi dışında `vbCFText` veya `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="a7a0a-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="a7a0a-106">Pano kullanarak `GetData` veya `SetData` yöntemi ile bir pano biçimi dışında `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="a7a0a-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="a7a0a-107">Kullanarak `GetData` veya `SetData` yöntemlerinin bir `DataObject` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılmış aralıktaki bir Pano biçimine sahip olduğunda bu pano biçimi değil kaydedilmedi Microsoft Windows ile .</span><span class="sxs-lookup"><span data-stu-id="a7a0a-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7a0a-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a7a0a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a7a0a-109">Geçersiz biçim kaldırın ve geçerli bir tane belirtin.</span><span class="sxs-lookup"><span data-stu-id="a7a0a-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a0a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a0a-110">See also</span></span>

- [<span data-ttu-id="a7a0a-111">Pano: Diğer biçimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a7a0a-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
