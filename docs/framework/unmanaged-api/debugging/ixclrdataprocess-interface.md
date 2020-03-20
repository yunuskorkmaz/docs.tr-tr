---
title: IXCLRDataProcess Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178371"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess Arabirimi

Bir işlem hakkında bilgi sorgulama yöntemleri sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                                                               | Açıklama                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Kendine `AppDomain` özgü kimliğiyle bir süreçten geçer.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Bir işlemin modüllerini sayısallandırmak için bir tutamaç sağlar.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Bu işlemin modüllerini oyalar.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Modül numaralandırması sırasında kullanılan dahili yinelemeciler tarafından kullanılan kaynakları serbest bırakır.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Belirli bir adresten `AppDomain` başlama yöntemi örneklerini sayısallandırmak için bir tutamaç sağlar. |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Bir adres mahsup adresinden başlayan bu işlemin yöntem örneklerini dizir.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Örnek numaralandırma sırasında kullanılan iç yinelemeciler tarafından kullanılan kaynakları söyler.             |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz. Ancak, her zamanki COM mekanizmaları ile `IUnknown` elde `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` edilebilir GUID ile türetilmiştir bir COM arayüzü.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).
**Üstbilgi:** Hiçbiri  
**Kütüphane:** Hiçbiri  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
