---
title: Pano biçimi geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: f2a0ab33c1749117d5de4987e85c44602ccd29ce
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245564"
---
# <a name="clipboard-format-is-not-valid"></a>Pano biçimi geçerli değil
Belirtilen Pano biçimi yürütülen yöntemi ile uyumlu değil. Bu hata için olası nedenler arasındadır:  
  
-   Pano kullanarak `GetText` veya `SetText` yöntemi ile bir pano biçimi dışında `vbCFText` veya `vbCFLink`.  
  
-   Pano kullanarak `GetData` veya `SetData` yöntemi ile bir pano biçimi dışında `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.  
  
-   Kullanarak `GetData` veya `SetData` yöntemlerinin bir `DataObject` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılmış aralıktaki bir Pano biçimine sahip olduğunda bu pano biçimi değil kaydedilmedi Microsoft Windows ile .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Geçersiz biçim kaldırın ve geçerli bir tane belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Pano: Diğer Biçimleri Ekleme](/cpp/mfc/clipboard-adding-other-formats)
