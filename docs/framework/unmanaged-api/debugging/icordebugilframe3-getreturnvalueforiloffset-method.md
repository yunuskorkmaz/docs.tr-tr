---
title: ICorDebugILFrame3::GetReturnValueForILOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset Metodu
Bir işlevin dönüş değeri yalıtan bir "ICorDebugValue" nesneyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ILOffset`  
 IL uzaklığı. Açıklamalar bölümüne bakın.  
  
 `ppReturnValue`  
 İşlev çağrısının dönüş değerini hakkında bilgi sağlayan bir "ICorDebugValue" arabirimi nesne adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile birlikte kullanılan [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir yönteminin dönüş değeri almak için yöntemi. Dönüş değerleri yoksayılır, aşağıdaki iki kod örneklerde olduğu gibi yöntemleri durumunda özellikle yararlı olacaktır. İlk örnek çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi, ancak yöntemin dönüş değeri yok sayıyor.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 İkinci örnek hata ayıklama içinde daha yaygın bir sorun gösterilmektedir. Yöntem çağrısı bir bağımsız değişken olarak kullanılan bir yöntem için dönüş değerini yalnızca hata ayıklayıcı çağrılan yöntemin adımları zaman erişilebilir. Özellikle çağrılan yöntemi bir harici kitaplık tanımlandığında çoğu durumda, mümkün değildir.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Geçirirseniz [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir işlev çağrısı siteye uzaklığı IL bir yöntemi, bir veya daha fazla yerel uzaklıklarını döndürür. Hata ayıklayıcı kesme noktaları bu yerel uzaklıkları işlevinde sonra ayarlayabilirsiniz. Hata ayıklayıcı kesme noktaları geldiğinde dönüş değeri almak için bu yönteme geçirilen aynı IL uzaklığı sonra geçirebilirsiniz. Hata ayıklayıcı sonra ayarlayın kesme noktaları temizlemeniz gerekir.  
  
> [!WARNING]
>  [Icordebugcode3::getreturnvalueliveoffset yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri dönüş değeri bilgilerini edinin izin verir. Değer türlerinden dönüş değeri bilgileri alınıyor (diğer bir deyişle, türetilen tüm türleri <xref:System.ValueType>) desteklenmiyor.  
  
 Tarafından belirtilen IL uzaklığı `ILOffset` parametresi bir işlev çağrısı sitede olmalıdır ve ayıklayıcı tarafından döndürülen yerel uzaklığında bir kesme adresindeki durdurulmalıdır [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL uzaklığı. Belirtilen IL uzaklığı için doğru konumda ayıklayıcı durdurulmaz API başarısız olur.  
  
 İşlev çağrısı bir değer döndürmüyor API başarısız olur.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetReturnValueLiveOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [ICorDebugILFrame3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
