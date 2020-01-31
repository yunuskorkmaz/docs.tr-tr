---
title: IXCLRDataMethodInstance Arabirimi
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790418"
---
# <a name="ixclrdatamethodinstance-interface"></a>IXCLRDataMethodInstance Arabirimi

Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                                  | Açıklama                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [Getıladdressmap](ixclrdatamethodinstance-getiladdressmap-method.md) | Eşleme bilgilerini ele almak için Il 'yi alır. |
| [GetRepresentativeEntryAddress](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır. |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, normal COM mekanizmalarından elde edilebilir GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` `IUnknown` türetilen bir COM arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
