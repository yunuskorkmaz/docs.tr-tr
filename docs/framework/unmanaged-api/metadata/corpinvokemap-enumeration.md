---
title: CorPinvokeMap Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079636"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap Numaralandırması
PInvoke arama seçeneklerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pmNoMangle`|Belirtilen üye adları kullanın.|  
|`pmCharSetMask`|Ayrılmış.|  
|`pmCharSetNotSpec`|Ayrılmış.|  
|`pmCharSetAnsi`|Birden çok baytlı karakter dizeleri olarak dizelerini sıralama.|  
|`pmCharSetUnicode`|2 baytlık karakterler Unicode dizelerini sıralama.|  
|`pmCharSetAuto`|Otomatik olarak hedef işletim sistemi için uygun şekilde dizeleri sıralaması. Varsayılan Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesinin Unicode bulunur. Windows 98 ve Windows Me ANSI varsayılandır|  
|`pmBestFitUseAssem`|Ayrılmış.|  
|`pmBestFitEnabled`|En iyi uyan eşlemeyi ANSI karakter kümesi içinde bir tam eşleşme eksik Unicode karakter gerçekleştirin.|  
|`pmBestFitDisabled`|Unicode karakter en iyi uyan eşlemeyi gerçekleştirmeyin. Bu durumda, tüm eşlenemez karakterleri ile değiştirilecek bir '?'.|  
|`pmBestFitMask`|Ayrılmış.|  
|`pmThrowOnUnmappableCharUseAssem`|Ayrılmış.|  
|`pmThrowOnUnmappableCharEnabled`|Birlikte çalışma sıralayıcısı eşlenemez bir karakterle karşılaştığında bir özel durum.|  
|`pmThrowOnUnmappableCharDisabled`|Birlikte çalışma sıralayıcısı eşlenemez bir karakterle karşılaştığında bir özel durum oluşturması beklenmiyor.|  
|`pmThrowOnUnmappableCharMask`|Ayrılmış|  
|`pmSupportsLastError`|Win32 çağırmak Aranan izin `SetLastError` öznitelikli yöntemini döndürmeden önce işlevi.|  
|`pmCallConvMask`|Ayrılmış|  
|`pmCallConvWinapi`|Varsayılan platform çağırma kuralını kullanın. Örneğin, Windows üzerinde varsayılandır `StdCall` ve Windows CE olduğu .NET `Cdecl`.|  
|`pmCallConvCdecl`|Kullanım `Cdecl` çağırma kuralı. Bu durumda, çağıranın yığını temizler. Bu, arama işlevlerinde sağlar `varargs` (diğer bir deyişle, değişik sayıda parametreyi kabul eden işlevler).|  
|`pmCallConvStdcall`|Kullanım `StdCall` çağırma kuralı. Bu durumda, çağrılan yığını temizler. Bu, yönetilmeyen işlevleri çağırma platformuyla çağırmak için varsayılan kuralıdır.|  
|`pmCallConvThiscall`|Kullanım `ThisCall` çağırma kuralı. Bu durumda ilk parametresinin olup `this` işaretçisi ve kayıtta ECX depolanır. Diğer parametreler, yığın üzerine itilir. `ThisCall` Çağırma yöntemleri yönetilmeyen DLL dosyasından dışarı aktarılan sınıflar çağırmak için kullanılır.|  
|`pmCallConvFastcall`|Ayrılmış.|  
|`pmMaxValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
