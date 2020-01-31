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
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790369"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess Arabirimi

İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                                                               | Açıklama                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [Getappdomainbyuniqueıd](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Bir işlemdeki `AppDomain` benzersiz kimliğine göre alır.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Bu işlemin modüllerini numaralandırır.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.               |
| [Startenummethodınstancesbyaddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Verilen bir adresten başlayarak `AppDomain` metot örneklerini numaralandırmak için bir tanıtıcı sağlar. |
| [Enummethodınstancebyaddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.                  |
| [Endenummethodınstancesbyaddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.             |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, normal COM mekanizmalarından elde edilebilir GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` `IUnknown` türetilen bir COM arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).   
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
