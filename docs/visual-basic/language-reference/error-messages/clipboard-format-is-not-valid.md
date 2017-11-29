---
title: "Pano biçimi geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="1bf80-102">Pano biçimi geçerli değil</span><span class="sxs-lookup"><span data-stu-id="1bf80-102">Clipboard format is not valid</span></span>
<span data-ttu-id="1bf80-103">Belirtilen Pano biçimi yürütülmekte yöntemi ile uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="1bf80-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="1bf80-104">Bu hatanın olası nedenleri arasında aşağıdakiler vardır:</span><span class="sxs-lookup"><span data-stu-id="1bf80-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="1bf80-105">Pano kullanarak `GetText` veya `SetText` dışında bir pano biçimi yöntemiyle `vbCFText` veya `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="1bf80-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="1bf80-106">Pano kullanarak `GetData` veya `SetData` dışında bir pano biçimi yöntemiyle `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="1bf80-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="1bf80-107">Kullanarak `DataObject``GetData` yöntemi veya `SetData` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılan aralıkla Pano biçiminde yöntemiyle ne zaman bu pano biçimi kaydettirilemedi Microsoft Windows ile.</span><span class="sxs-lookup"><span data-stu-id="1bf80-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bf80-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1bf80-108">To correct this error</span></span>  
  
-   <span data-ttu-id="1bf80-109">Geçersiz biçim kaldırın ve geçerli bir tane belirtin.</span><span class="sxs-lookup"><span data-stu-id="1bf80-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf80-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf80-110">See Also</span></span>  
 [<span data-ttu-id="1bf80-111">Pano: Diğer biçimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1bf80-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
