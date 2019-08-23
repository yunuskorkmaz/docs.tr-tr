---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ea68474a1ee3a856b2e9393ff67d44f40a471c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911435"
---
# <a name="icordebugdatatarget2-interface"></a>ICorDebugDataTarget2 Arabirimi
[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateVirtualUnwinder Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.|  
|[EnumerateThreadIDs Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|Etkin iş parçacığı kimliklerinin bir listesini döndürür.|  
|[GetImageFromPointer Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.|  
|[GetImageLocation Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|Modülün temel adresinden bir modülün yolunu döndürür.|  
|[GetSymbolProviderForImage Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
