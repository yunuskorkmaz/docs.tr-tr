---
title: CorSymAddrKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: f71d8956e8706cdc71b94b6e6e2e8210e5b9161e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725241"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind Numaralandırması

Bellek adresi türünü gösterir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Bir Microsoft ara dili (MSIL) yerel değişkenini veya parametre dizinini gösterir.|  
|`ADDR_NATIVE_RVA`|Bir modülün göreli bir sanal adresini gösterir.|  
|`ADDR_NATIVE_REGISTER`|Bir CPU kaydını gösterir.|  
|`ADDR_NATIVE_REGREL`|İlk adresin bir kayıt olduğunu ve ikinci adresin bir konum olduğunu gösterir.|  
|`ADDR_NATIVE_OFFSET`|Temel adresten bir konum gösterir.|  
|`ADDR_NATIVE_REGREG`|İlk adresin kaydın alt kısmı olduğunu ve ikinci adresin ise yüksek bir kısmını gösterir.|  
|`ADDR_NATIVE_REGSTK`|İlk adresin bir kaydın alt kısmı olduğunu, ikincinin Yüksek kısmını ve üçüncüsü de bir konum olduğunu gösterir.|  
|`ADDR_NATIVE_STKREG`|İlk adresin bir yazmaç olduğunu, ikincinin bir konum olduğunu ve üçüncü öğenin, kaydın yüksek kısmıdır olduğunu gösterir.|  
|`ADDR_BITFIELD`|İlk adresin bir alanın başlangıcı olduğunu ve ikinci adresin alan uzunluğu olduğunu gösterir.|  
|`ADDR_NATIVE_ISECTOFFSET`|İlk adresin bölüm olduğunu ve ikinci adresin bir konum olduğunu gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Numaralandırmaları](diagnostics-symbol-store-enumerations.md)
