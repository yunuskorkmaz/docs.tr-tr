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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425411"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind Numaralandırması
Bellek adresi türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`ADDR_IL_OFFSET`|Bir Microsoft Ara dili (MSIL) yerel değişken veya parametre dizinini gösterir.|  
|`ADDR_NATIVE_RVA`|Göreli sanal adres bir modüle gösterir.|  
|`ADDR_NATIVE_REGISTER`|Bir CPU kayıt gösterir.|  
|`ADDR_NATIVE_REGREL`|Bir kayıt ilk adresi olduğunu ve bir uzaklık ikinci adresidir gösterir.|  
|`ADDR_NATIVE_OFFSET`|Temel adres uzaklık gösterir.|  
|`ADDR_NATIVE_REGREG`|İlk adres düşük bir kayıt bölümüdür ve yüksek bölümü ikinci adresidir gösterir.|  
|`ADDR_NATIVE_REGSTK`|İlk adres düşük bir kayıt bölümüdür, ikinci yüksek bölümüdür ve üçüncü bir uzaklığı belirtir.|  
|`ADDR_NATIVE_STKREG`|Bir kayıt ilk adresidir, ikinci bir uzaklığı ve üçüncü kayıt yüksek bölümüdür gösterir.|  
|`ADDR_BITFIELD`|İlk adres alanının başlangıç ve ikinci adresi alan uzunluğu olduğunu gösterir.|  
|`ADDR_NATIVE_ISECTOFFSET`|İlk adres bölümdür ve bir uzaklık ikinci adresidir gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
