---
title: ISOSDacInterface Arabirimi
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790474"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface Arabirimi

`SOS`verilere erişmek için yardımcı yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                               | Açıklama                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | Verilen MethodDesc işaretçisi için verileri alır. |
| [Getmethoddescptrfromıp](isosdacinterface-getmethoddescptrfromip-method.md) | Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır. |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| Verilen bir adreste yüklü olan modüle karşılık gelen verileri getirir. |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, normal COM mekanizmalarından elde edilebilir GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` `IUnknown` türetilen bir COM arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
