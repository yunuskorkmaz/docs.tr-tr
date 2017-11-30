---
title: "CorSymAddrKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bb55d9c9f85ae8f8112f16dcf552295699826d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Tanılama sembol deposu numaralandırmaları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
