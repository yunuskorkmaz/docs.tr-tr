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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007552"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap Numaralandırması
PInvoke çağrısı seçeneklerini belirtir.  
  
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
|`pmNoMangle`|Her üye adını belirtilen şekilde kullanın.|  
|`pmCharSetMask`|Ayrılmış.|  
|`pmCharSetNotSpec`|Ayrılmış.|  
|`pmCharSetAnsi`|Dizeleri birden çok baytlık karakter dizesi olarak sıralama.|  
|`pmCharSetUnicode`|Dizeleri Unicode 2 baytlık karakterler olarak sıralama.|  
|`pmCharSetAuto`|Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak sıralama. Varsayılan değer Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesi için Unicode 'dur; Varsayılan değer Windows 98 ve Windows Me 'de ANSI 'dir.|  
|`pmBestFitUseAssem`|Ayrılmış.|  
|`pmBestFitEnabled`|ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en iyi şekilde eşleşmesini gerçekleştirin.|  
|`pmBestFitDisabled`|Unicode karakterlerin en iyi şekilde eşleşmesini gerçekleştirmeyin. Bu durumda, tüm eşlenebilir karakterler '? ' ile değiştirilirler.|  
|`pmBestFitMask`|Ayrılmış.|  
|`pmThrowOnUnmappableCharUseAssem`|Ayrılmış.|  
|`pmThrowOnUnmappableCharEnabled`|Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında bir özel durum oluşturur.|  
|`pmThrowOnUnmappableCharDisabled`|Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında özel durum oluşturmaz.|  
|`pmThrowOnUnmappableCharMask`|Ayrıldı|  
|`pmSupportsLastError`|Aranan `SetLastError` yöntemden dönmeden önce çağrılan tarafından Win32 işlevini çağırmaya izin verin.|  
|`pmCallConvMask`|Ayrıldı|  
|`pmCallConvWinapi`|Varsayılan platform çağırma kuralını kullanın. Örneğin, Windows 'ta varsayılan olarak `StdCall` ve Windows CE .net ' dir `Cdecl` .|  
|`pmCallConvCdecl`|`Cdecl`Çağırma kuralını kullanın. Bu durumda, çağıran yığını temizler. Bu, işlevleri çağırma `varargs` (diğer bir deyişle, değişken sayıda parametre kabul eden işlevler) sunar.|  
|`pmCallConvStdcall`|`StdCall`Çağırma kuralını kullanın. Bu durumda, çağrılan yığını temizler. Bu, platform Invoke ile yönetilmeyen işlevleri çağırmak için varsayılan kuraldır.|  
|`pmCallConvThiscall`|`ThisCall`Çağırma kuralını kullanın. Bu durumda, ilk parametre `this` işaretçisidir ve Register ECX konumunda depolanır. Diğer parametreler yığına gönderilir. `ThisCall`Çağırma kuralı, yönetilmeyen BIR DLL 'den aktarılmış sınıflarda yöntemleri çağırmak için kullanılır.|  
|`pmCallConvFastcall`|Ayrılmış.|  
|`pmMaxValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
