---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 472ea0b3d54c025cdd69957765ad2663c7288b15
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783565"
---
# <a name="icordebugdatatarget2-interface"></a>ICorDebugDataTarget2 Arabirimi
[ICorDebugDataTarget](icordebugdatatarget-interface.md)arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateVirtualUnwinder Yöntemi](icordebugdatatarget2-createvirtualunwinder-method.md)|Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.|  
|[EnumerateThreadIDs Yöntemi](icordebugdatatarget2-enumeratethreadids-method.md)|Etkin iş parçacığı kimliklerinin bir listesini döndürür.|  
|[GetImageFromPointer Yöntemi](icordebugdatatarget2-getimagefrompointer-method.md)|Bu modüldeki bir adresten modül taban adresini ve boyutunu döndürür.|  
|[GetImageLocation Yöntemi](icordebugdatatarget2-getimagelocation-method.md)|Modülün temel adresinden bir modülün yolunu döndürür.|  
|[GetSymbolProviderForImage Yöntemi](icordebugdatatarget2-getsymbolproviderforimage-method.md)|Bu modülün temel adresinden bir modülün sembol sağlayıcısını döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
