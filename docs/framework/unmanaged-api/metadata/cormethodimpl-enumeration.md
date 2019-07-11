---
title: CorMethodImpl Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c88c12646a13e5a24f2475bd2db04c8c831141c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781761"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl Numaralandırması
Yöntem uygulama özellikleri açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`miCodeTypeMask`|Kod türünü tanımlayan bayraklar.|  
|`miIL`|Yöntem uygulaması, Microsoft Ara dilini (MSIL) olduğunu belirtir.|  
|`miNative`|Yöntem uygulaması yerel olduğunu belirtir.|  
|`miOPTIL`|Yöntem uygulaması OPTIL olduğunu belirtir.|  
|`miRuntime`|Yöntem uygulaması ortak dil çalışma zamanı tarafından sağlandığını belirtir.|  
|`miManagedMask`|Kod yönetilen veya yönetilmeyen olup olmadığını belirten bayrak.|  
|`miUnmanaged`|Yöntem uygulaması yönetilmeyen olduğunu belirtir.|  
|`miManaged`|Yöntem uygulaması yönetilir belirtir.|  
|`miForwardRef`|Yöntemin tanımlandığı belirtir. Bu bayrak öncelikle birleştirme senaryolarda kullanılır.|  
|`miPreserveSig`|Yöntem imzası bir HRESULT dönüştürme için karıştırılmış belirtir.|  
|`miInternalCall`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`miSynchronized`|Yöntemin gövdesinde tek hiper iş parçacıklı olduğunu belirtir.|  
|`miNoInlining`|Yöntem satır içine alınmış olamaz belirtir.|  
|`miAggressiveInlining`|Yöntem mümkünse satır içine alınmış olması gerektiğini belirtir.|  
|`miNoOptimization`|Yöntem getirilmemiş belirtir.|  
|`miMaxMethodImplVal`|Geçerli değeri en fazla bir `CorMethodImpl`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
