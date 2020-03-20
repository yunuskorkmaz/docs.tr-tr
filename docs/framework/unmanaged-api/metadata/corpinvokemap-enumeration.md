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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176155"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap Numaralandırması
Bir PInvoke araması için seçenekleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`pmNoMangle`|Belirtilen her üye adını kullanın.|  
|`pmCharSetMask`|Ayrılmış.|  
|`pmCharSetNotSpec`|Ayrılmış.|  
|`pmCharSetAnsi`|Mareşal dizeleri çoklu bayt karakter dizeleri olarak.|  
|`pmCharSetUnicode`|Unicode 2-bayt karakterleri olarak Mareşal dizeleri.|  
|`pmCharSetAuto`|Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak mareşal. Varsayılan olarak Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesindeki Unicode; varsayılan Windows 98 ve Windows Me'deki ANSI'dir.|  
|`pmBestFitUseAssem`|Ayrılmış.|  
|`pmBestFitEnabled`|ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en uygun eşlenemesini gerçekleştirin.|  
|`pmBestFitDisabled`|Unicode karakterlerinin en uygun eşlemesi gerçekleştirmeyin. Bu durumda, eşlenemeyecek tüm karakterler '?' ile değiştirilir.|  
|`pmBestFitMask`|Ayrılmış.|  
|`pmThrowOnUnmappableCharUseAssem`|Ayrılmış.|  
|`pmThrowOnUnmappableCharEnabled`|Interop mareşal eşlenebilir bir karakter karşılaştığında bir özel durum atın.|  
|`pmThrowOnUnmappableCharDisabled`|Interop mareşal eşlenebilir bir karakter karşılaştığında bir özel durum atmayın.|  
|`pmThrowOnUnmappableCharMask`|Ayrıldı|  
|`pmSupportsLastError`|Atfedilen yöntemden dönmeden önce `SetLastError` callee'nin Win32 işlevini aramasına izin verin.|  
|`pmCallConvMask`|Ayrıldı|  
|`pmCallConvWinapi`|Varsayılan çağrı kuralını kullanın. Örneğin, Windows'da varsayılan `StdCall` ve Windows CE .NET'te . `Cdecl`|  
|`pmCallConvCdecl`|Arama `Cdecl` kuralını kullanın. Bu durumda, arayan yığını temizler. Bu, (değişken `varargs` sayıda parametre kabul eden işlevler) ile arama işlevlerini etkinleştirmektedir.|  
|`pmCallConvStdcall`|Arama `StdCall` kuralını kullanın. Bu durumda, callee yığını temizler. Bu, yönetilmeyen işlevleri platform çağrısıyla çağırmak için varsayılan kuraldır.|  
|`pmCallConvThiscall`|Arama `ThisCall` kuralını kullanın. Bu durumda, ilk parametre `this` işaretçidir ve kayıt ECX'te depolanır. Diğer parametreler yığına itilir. Çağrı `ThisCall` kuralı, yönetilmeyen bir DLL'den dışa aktarılan sınıflardaki yöntemleri çağırmak için kullanılır.|  
|`pmCallConvFastcall`|Ayrılmış.|  
|`pmMaxValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorHdr.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
