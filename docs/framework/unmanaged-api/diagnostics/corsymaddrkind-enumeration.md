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
ms.openlocfilehash: 389cf2e77728002ce1078f63df3d741d1847c105
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744979"
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
|`ADDR_IL_OFFSET`|Bir Microsoft Ara dili (MSIL) yerel değişken veya parametre dizini belirtir.|  
|`ADDR_NATIVE_RVA`|Bir göreli sanal adres, bir modül olarak gösterir.|  
|`ADDR_NATIVE_REGISTER`|Bir CPU kaydı gösterir.|  
|`ADDR_NATIVE_REGREL`|Bir kayıt ilk adresidir ve bir uzaklık ikinci adresidir gösterir.|  
|`ADDR_NATIVE_OFFSET`|Temel adres bir uzaklığı belirtir.|  
|`ADDR_NATIVE_REGREG`|İlk adres bir kayıt düşük bölümüdür ve yüksek bölümü ikinci adresidir gösterir.|  
|`ADDR_NATIVE_REGSTK`|İlk adres bir kayıt düşük bölümüdür, ikinci yüksek bölümüdür ve üçüncü bir uzaklık olduğunu gösterir.|  
|`ADDR_NATIVE_STKREG`|Bir kayıt ilk adresidir, ikincisi ise bir uzaklık ve üçüncü kayıt yüksek bölümüdür gösterir.|  
|`ADDR_BITFIELD`|İlk adres alanının başlangıç ve ikinci adresini alan uzunluğu olduğunu gösterir.|  
|`ADDR_NATIVE_ISECTOFFSET`|İlk adres bölümdür ve bir uzaklık ikinci adresidir gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Tanılama Simge Deposu Sabit Listeleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
