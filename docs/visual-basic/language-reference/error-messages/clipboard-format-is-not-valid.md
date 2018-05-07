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
---
# <a name="clipboard-format-is-not-valid"></a>Pano biçimi geçerli değil
Belirtilen Pano biçimi yürütülmekte yöntemi ile uyumlu değil. Bu hatanın olası nedenleri arasında aşağıdakiler vardır:  
  
-   Pano kullanarak `GetText` veya `SetText` dışında bir pano biçimi yöntemiyle `vbCFText` veya `vbCFLink`.  
  
-   Pano kullanarak `GetData` veya `SetData` dışında bir pano biçimi yöntemiyle `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.  
  
-   Kullanarak `DataObject``GetData` yöntemi veya `SetData` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılan aralıkla Pano biçiminde yöntemiyle ne zaman bu pano biçimi kaydettirilemedi Microsoft Windows ile.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Geçersiz biçim kaldırın ve geçerli bir tane belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Pano: Diğer Biçimleri Ekleme](/cpp/mfc/clipboard-adding-other-formats)
