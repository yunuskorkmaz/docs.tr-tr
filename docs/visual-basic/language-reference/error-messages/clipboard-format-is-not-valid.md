---
title: "Pano biçimi geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a>Pano biçimi geçerli değil
Belirtilen Pano biçimi yürütülmekte yöntemi ile uyumlu değil. Bu hatanın olası nedenleri arasında aşağıdakiler vardır:  
  
-   Pano kullanarak `GetText` veya `SetText` dışında bir pano biçimi yöntemiyle `vbCFText` veya `vbCFLink`.  
  
-   Pano kullanarak `GetData` veya `SetData` dışında bir pano biçimi yöntemiyle `vbCFBitmap`, `vbCFDIB`, veya `vbCFMetafile`.  
  
-   Kullanarak `DataObject``GetData` yöntemi veya `SetData` kayıtlı biçimleri (HC000 - & HFFFF için), Microsoft Windows tarafından ayrılan aralıkla Pano biçiminde yöntemiyle ne zaman bu pano biçimi kaydettirilemedi Microsoft Windows ile.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Geçersiz biçim kaldırın ve geçerli bir tane belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Pano: Diğer biçimleri ekleme](/cpp/mfc/clipboard-adding-other-formats)
