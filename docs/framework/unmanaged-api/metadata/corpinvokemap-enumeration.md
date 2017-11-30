---
title: "CorPinvokeMap Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c6e1a49d18cde768884ab3d92eaa6593e2955c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap Numaralandırması
PInvoke çağrısı seçeneklerini belirtir.  
  
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
|`pmNoMangle`|Her üye adı belirtildiği şekilde kullanın.|  
|`pmCharSetMask`|Ayrılmış.|  
|`pmCharSetNotSpec`|Ayrılmış.|  
|`pmCharSetAnsi`|Birden çok baytlı karakter dizeleri olarak dizelerini sıralama.|  
|`pmCharSetUnicode`|Unicode 2-bayt karakter olarak dizelerini sıralama.|  
|`pmCharSetAuto`|Otomatik olarak hedef işletim sistemi için uygun şekilde dizeleri sıralama. Windows NT, Windows 2000, Windows XP ve Windows Server 2003 ailesinde Unicode varsayılandır; Windows 98 ve Windows Me ANSI varsayılandır|  
|`pmBestFitUseAssem`|Ayrılmış.|  
|`pmBestFitEnabled`|ANSI karakter kümesini içinde bir tam eşleşme olmaması Unicode karakterler, en uygun eşlemeyi gerçekleştirmek.|  
|`pmBestFitDisabled`|Unicode karakterler, en uygun eşlemeyi gerçekleştirmek değil. Bu durumda, tüm eşlenemez karakterleri tarafından değiştirilecek olan bir '?'.|  
|`pmBestFitMask`|Ayrılmış.|  
|`pmThrowOnUnmappableCharUseAssem`|Ayrılmış.|  
|`pmThrowOnUnmappableCharEnabled`|Birlikte çalışma Sıralayıcı eşlenemez karakter karşılaştığında bir özel durum.|  
|`pmThrowOnUnmappableCharDisabled`|Birlikte çalışma Sıralayıcı eşlenemez karakter karşılaştığında bir özel durum değil.|  
|`pmThrowOnUnmappableCharMask`|Ayrılmış|  
|`pmSupportsLastError`|Win32 çağırmak Aranan izin `SetLastError` öznitelikli yönteminden dönmeden önce işlevi.|  
|`pmCallConvMask`|Ayrılmış|  
|`pmCallConvWinapi`|Çağırma kuralı varsayılan platform kullanın. Örneğin, Windows varsayılandır `StdCall` ve Windows CE olduğu .NET `Cdecl`.|  
|`pmCallConvCdecl`|Kullanım `Cdecl` çağırma. Bu durumda, çağıranın yığını temizler. Bu arama işlevleri sağlar `varargs` (diğer bir deyişle, değişken bir dizi parametre kabul eden işlevler).|  
|`pmCallConvStdcall`|Kullanım `StdCall` çağırma. Bu durumda, aranan yığını temizler. Bu, yönetilmeyen işlevleri çağırma platformuyla çağırmak için varsayılan kuraldır.|  
|`pmCallConvThiscall`|Kullanım `ThisCall` çağırma. Bu durumda, ilk parametre olan `this` işaretçi ve ECX kayıttaki depolanır. Diğer parametreler yığına. `ThisCall` Çağırma yöntemleri yönetilmeyen DLL dosyasından dışarı sınıfları çağırmak için kullanılır.|  
|`pmCallConvFastcall`|Ayrılmış.|  
|`pmMaxValue`|Ayrılmış.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
