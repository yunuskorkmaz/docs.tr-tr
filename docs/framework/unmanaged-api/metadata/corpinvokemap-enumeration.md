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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441563"
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
|`pmCharSetMask`|Ayrılamadı.|  
|`pmCharSetNotSpec`|Ayrılamadı.|  
|`pmCharSetAnsi`|Dizeleri birden çok baytlık karakter dizesi olarak sıralama.|  
|`pmCharSetUnicode`|Dizeleri Unicode 2 baytlık karakterler olarak sıralama.|  
|`pmCharSetAuto`|Dizeleri hedef işletim sistemi için uygun şekilde otomatik olarak sıralama. Varsayılan değer Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesi için Unicode 'dur; Varsayılan değer Windows 98 ve Windows Me 'de ANSI 'dir.|  
|`pmBestFitUseAssem`|Ayrılamadı.|  
|`pmBestFitEnabled`|ANSI karakter kümesinde tam eşleşme olmayan Unicode karakterlerinin en iyi şekilde eşleşmesini gerçekleştirin.|  
|`pmBestFitDisabled`|Unicode karakterlerin en iyi şekilde eşleşmesini gerçekleştirmeyin. Bu durumda, tüm eşlenebilir karakterler '? ' ile değiştirilirler.|  
|`pmBestFitMask`|Ayrılamadı.|  
|`pmThrowOnUnmappableCharUseAssem`|Ayrılamadı.|  
|`pmThrowOnUnmappableCharEnabled`|Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında bir özel durum oluşturur.|  
|`pmThrowOnUnmappableCharDisabled`|Birlikte çalışma sıralayıcısı, eşlenebilir bir karakterle karşılaştığında özel durum oluşturmaz.|  
|`pmThrowOnUnmappableCharMask`|Ayrılmış|  
|`pmSupportsLastError`|Aranan yöntemden dönmeden önce çağrılan tarafından Win32 `SetLastError` işlevini çağırmaya izin verin.|  
|`pmCallConvMask`|Ayrılmış|  
|`pmCallConvWinapi`|Varsayılan platform çağırma kuralını kullanın. Örneğin, Windows 'da varsayılan değer `StdCall` ve Windows CE .NET ' de `Cdecl`.|  
|`pmCallConvCdecl`|`Cdecl` çağırma kuralını kullanın. Bu durumda, çağıran yığını temizler. Bu, işlevleri `varargs` (bir değişken parametre sayısı kabul eden işlevler) ile çağırma imkanı sunar.|  
|`pmCallConvStdcall`|`StdCall` çağırma kuralını kullanın. Bu durumda, çağrılan yığını temizler. Bu, platform Invoke ile yönetilmeyen işlevleri çağırmak için varsayılan kuraldır.|  
|`pmCallConvThiscall`|`ThisCall` çağırma kuralını kullanın. Bu durumda, ilk parametre `this` işaretçisidir ve Register ECX konumunda depolanır. Diğer parametreler yığına gönderilir. `ThisCall` çağırma kuralı, yönetilmeyen bir DLL 'den aktarılmış sınıflarda yöntemleri çağırmak için kullanılır.|  
|`pmCallConvFastcall`|Ayrılamadı.|  
|`pmMaxValue`|Ayrılamadı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
