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
# <a name="clipboard-format-is-not-valid"></a>Pano biçimi geçerli değil

Belirtilen Pano biçimi yürütülmekte olan yöntemle uyumsuz. Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:  
  
- `GetText` `SetText` Veya dışında bir pano biçimiyle pano veya yöntemini kullanma `vbCFText` `vbCFLink` .  
  
- Panonun `GetData` veya `SetData` yönteminin, veya dışında bir pano biçimiyle kullanılması `vbCFBitmap` `vbCFDIB` `vbCFMetafile` .  
  
- , `GetData` `SetData` `DataObject` Pano biçimi Microsoft Windows 'a kaydedilmediği zaman, kayıtlı BIÇIMLER (&HC000-&hffff) için Microsoft Windows tarafından ayrılmış aralıktaki bir pano biçimiyle veya yöntemlerini kullanma.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Geçersiz biçimi kaldırın ve geçerli bir tane belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Pano: diğer biçimleri ekleme](/cpp/mfc/clipboard-adding-other-formats)
