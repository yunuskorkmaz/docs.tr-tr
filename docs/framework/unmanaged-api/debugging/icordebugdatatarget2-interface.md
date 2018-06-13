---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85ff64e30519e448b87c2e9ae5d2c66959d836fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412139"
---
# <a name="icordebugdatatarget2-interface"></a>ICorDebugDataTarget2 Arabirimi
Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateVirtualUnwinder Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.|  
|[EnumerateThreadIDs Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|Etkin iş parçacığı kimlikleri listesini döndürür.|  
|[GetImageFromPointer Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|Bu modüldeki bir adresinden modülü taban adresi ve boyutu döndürür.|  
|[GetImageLocation Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|Yolun bir modül modülün temel adresinden döndürür.|  
|[GetSymbolProviderForImage Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|Bir modül için simge sağlayıcısı bu modül temel adresinden döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET yerel ile kullanılabilir. Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
