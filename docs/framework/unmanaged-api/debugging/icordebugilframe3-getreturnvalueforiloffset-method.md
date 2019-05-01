---
title: ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ac90473a0bf15173683c45abc8e4a840ea7e733
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946443"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
Bir işlevin dönüş değeri bir "ICorDebugValue" nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ILOffset`  
 IL uzaklığı. Açıklamalar bölümüne bakın.  
  
 `ppReturnValue`  
 Bir işlev çağrısının döndürme değeri hakkında bilgi sağlayan bir "ICorDebugValue" arabirim nesnesinin adresine bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile birlikte kullanılan [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir yöntemin dönüş değerini almak için yöntemi. Dönüş değerleri, aşağıdaki iki kod örneği gibi yöntemler özellikle faydalıdır. İlk örneği çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi, ancak yöntemin dönüş değerini yoksayar.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 İkinci örnek hata ayıklamada çok daha yaygın bir sorunu gösterir. Bir yöntem, yöntem çağrısında bağımsız değişken olarak kullanıldığından dönüş değeri, yalnızca hata ayıklayıcı çağrılan yöntem üzerinden adımları olduğunda da erişilebilir. Özellikle çağrılan yöntem bir harici kitaplık olarak tanımlandığında çoğu durumda, mümkün değildir.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Geçirirseniz [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir işlev çağrısı siteye IL uzaklığı bir yöntemi, bir veya daha fazla yerel uzaklıklar verir. Hata ayıklayıcı, ardından işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilirsiniz. Hata ayıklayıcı kesme noktalarından birine eriştiğinde, dönüş değeri almak için bu yönteme geçilen aynı IL uzaklığını geçirebilirsiniz. Ardından hata ayıklayıcıyı ayarladığı tüm kesme noktalarını temizlemeniz gerekir.  
  
> [!WARNING]
>  [Icordebugcode3::getreturnvalueliveoffset metodu](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanıza olanak tanır. Değer türlerinden dönüş değeri bilgilerini alma (diğer bir deyişle, öğesinden türetilen tüm türler <xref:System.ValueType>) desteklenmiyor.  
  
 Tarafından belirtilen IL uzaklığı `ILOffset` parametresi bir işlev çağrısı sitesinde olmalıdır ve hata ayıklanan adresindeki tarafından döndürülen yerel uzaklıkta ayarlanan bir kesme noktasında durdurulmalıdır [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL uzaklığı için. Hata ayıklanan belirtilen IL uzaklığı için doğru konumda durdurulmamışsa API başarısız olur.  
  
 İşlev çağrısı bir değer döndürmezse API başarısız olur.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemlerinde.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetReturnValueLiveOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
