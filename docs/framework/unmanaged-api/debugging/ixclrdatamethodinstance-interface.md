---
description: 'Daha fazla bilgi edinin: IXCLRDataMethodInstance Interface'
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
ms.openlocfilehash: 4e9ad57988420ff14b297c693c31c0dc5b3b181c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800792"
---
# <a name="ixclrdatamethodinstance-interface"></a>IXCLRDataMethodInstance Arabirimi

Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                                  | Açıklama                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [GetILAddressMap](ixclrdatamethodinstance-getiladdressmap-method.md) | Eşleme bilgilerini ele almak için Il 'yi alır. |
| [GetRepresentativeEntryAddress](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | Bir yöntem için tüm olası giriş noktalarının yerel derlenmesi için en temsili giriş noktası adresini alır. |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, `IUnknown` `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
