---
title: "CorMethodImpl Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl Numaralandırması
Yöntem uygulaması özellikleri açıklanmaktadır değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`miCodeTypeMask`|Kod türünü açıklayan bayrakları.|  
|`miIL`|Yöntem uygulaması Microsoft Ara dili (MSIL) olduğunu belirtir.|  
|`miNative`|Yöntem uygulaması yerel olduğunu belirtir.|  
|`miOPTIL`|Yöntem uygulaması OPTIL olduğunu belirtir.|  
|`miRuntime`|Yöntem uygulaması ortak dil çalışma zamanı tarafından sağlandığını belirtir.|  
|`miManagedMask`|Kod yönetilen veya yönetilmeyen olup olmadığını belirten bayrak.|  
|`miUnmanaged`|Yöntem uygulaması yönetilmeyen olduğunu belirtir.|  
|`miManaged`|Yöntem uygulaması yönetilip yönetilmediğini belirtir.|  
|`miForwardRef`|Yöntemi tanımlanır belirtir. Bu bayrak, öncelikle birleştirme senaryolarda kullanılır.|  
|`miPreserveSig`|Yöntem imzası HRESULT dönüştürme için karıştırılmış belirtir.|  
|`miInternalCall`|İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.|  
|`miSynchronized`|Yöntemi, tek kendi gövde iş parçacıklı olduğunu belirtir.|  
|`miNoInlining`|Yöntem içermesinden olamaz belirtir.|  
|`miAggressiveInlining`|Yöntemi, mümkünse içermesinden olması gerektiğini belirtir.|  
|`miNoOptimization`|Yöntem getirilmemiş belirtir.|  
|`miMaxMethodImplVal`|Geçerli değeri en fazla bir `CorMethodImpl`.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
