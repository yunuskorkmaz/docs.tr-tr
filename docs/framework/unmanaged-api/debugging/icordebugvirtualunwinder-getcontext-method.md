---
description: 'Daha fazla bilgi edinin: ICorDebugVirtualUnwinder:: GetContext yöntemi'
title: 'ICorDebugVirtualUnwinder:: GetContext yöntemi'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: 864f32ce82149658b2d4a617b08e8d7aa41fe642
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790535"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder:: GetContext yöntemi

Bu unwinder 'in geçerli bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `contextFlags`  
 'ndaki İçeriğin hangi bölümlerinin döndürüleceği (WinNT. h içinde tanımlanır) belirleyen bayraklar.  
  
 `cbContextBuf`  
 'ndaki İçindeki bayt sayısı `contextBuf` .  
  
 `contextSize`  
 dışı Gerçekten üzerine yazılan bayt sayısına yönelik bir işaretçi `contextBuf` .  
  
 `contextBuf`  
 dışı Bu unwinder 'in geçerli bağlamını içeren bir bayt dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Mscordbi tarafından alınan başarısız olan HRESULT değeri, önemli olarak değerlendirilir ve ICorDebug API 'Lerinin dönmesini sağlar `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Açıklamalar  

 `contextBuf`Bağımsız değişkenin başlangıç değerini [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) yöntemini çağırarak döndürülen bağlam arabelleğine ayarlarsınız.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
 Geri sarma, yalnızca geçici olmayan Yazmaçları gibi yazmaçların bir alt kümesini geri yükleyebilir, çünkü bağlam gerçek Yöntem çağrısı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
