---
title: ICorProfilerInfo5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ba082182ec7e2f639ef94baeb29203ee792fba0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455334"
---
# <a name="icorprofilerinfo5-interface"></a>ICorProfilerInfo5 Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Öğesinin bir alt [Icorprofilerınfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) ortak dil çalışma olayı izleme denetlemek için (CLR) ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|Profil Oluşturucu CLR bildirimlerini almak istediği geçerli olay kategorileri alır.|  
|[SetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|Profil Oluşturucu CLR olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirimde yöntemleri değiştirmek için tasarlanmıştır [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) ve [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
