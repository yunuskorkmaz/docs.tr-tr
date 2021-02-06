---
description: ': Icordebugmergedassemblyrecord arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: e64c0ee30a8e8956dd336a30e6c81962c75f04e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650306"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord Arabirimi

Birleştirilmiş bir derleme hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCulture Yöntemi](icordebugmergedassemblyrecord-getculture-method.md)|Derlemenin kültür adı dizesini alır.|  
|[GetIndex Yöntemi](icordebugmergedassemblyrecord-getindex-method.md)|Derlemenin önek dizinini alır.|  
|[GetPublicKey Yöntemi](icordebugmergedassemblyrecord-getpublickey-method.md)|Derlemenin ortak anahtarını alır.|  
|[GetPublicKeyToken Metodu](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Derlemenin ortak anahtar belirtecini alır.|  
|[GetSimpleName Yöntemi](icordebugmergedassemblyrecord-getsimplename-method.md)|Derlemenin basit adını alır.|  
|[GetVersion Yöntemi](icordebugmergedassemblyrecord-getversion-method.md)|Derlemenin sürüm bilgilerini alır.|  
  
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
