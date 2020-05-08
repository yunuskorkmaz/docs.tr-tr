---
title: ICorDebugDataTarget2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 1c598d23cac77e50cf302e6936b88b5eb6e558c2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976441"
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
