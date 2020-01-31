---
title: IXCLRDataMethodDefinition Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790421"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition Arabirimi

Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

Aşağıdaki yöntemler, arabiriminde kullanılabilen yöntemlerin bazılarıdır.

| Yöntem                                                                                                                          | Açıklama                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [Startenumınstances](ixclrdatamethoddefinition-startenuminstances-method.md) | Belirli bir `IXCLRDataAppDomain`için yöntem örneklerinin numaralandırılması için bir tanıtıcı sağlar. |
| [Enumınstance](ixclrdatamethoddefinition-enuminstance-method.md)             | Bu yöntem tanımının örneklerini numaralandırır.                                         |
| [Endenumınstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.         |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, normal COM mekanizmalarından elde edilebilir GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` `IUnknown` türetilen bir COM arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
