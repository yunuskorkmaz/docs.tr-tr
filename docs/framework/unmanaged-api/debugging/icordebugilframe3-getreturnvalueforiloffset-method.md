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
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178811"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
Bir işlevin geri dönüş değerini kapsülleyen bir "ICorDebugValue" nesnesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ILOffset`  
 IL ofset. Açıklamalar bölümüne bakın.  
  
 `ppReturnValue`  
 İşlev çağrısının geri dönüş değeri hakkında bilgi sağlayan "ICorDebugValue" arabirimi nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir yöntemin geri dönüş değerini almak için [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi ile birlikte kullanılır. Özellikle, aşağıdaki iki kod örneğinde olduğu gibi, iade değerleri göz ardı edilen yöntemler de yararlıdır. İlk örnek <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi çağırır, ancak yöntemin geri dönüş değerini yoksa.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 İkinci örnek, hata ayıklamada çok daha yaygın bir sorunu göstermektedir. Yöntem çağrısında bağımsız değişken olarak kullanıldığından, geri dönüş değerine yalnızca çağrıyı çağıran yöntem üzerinden hata ayıklama adımı attığında erişilebilir. Birçok durumda, özellikle çağrılan yöntem dış kitaplıkta tanımlandığında, bu mümkün değildir.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemini bir işlev arama sitesine IL ofset'i geçerseniz, bir veya daha fazla yerel uzaklık döndürür. Hata ayıklama, işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilir. Hata ayıklama kesme noktalarından birine çarptığında, iade değerini almak için bu yönteme geçtiğiniz IL ofsetini geçebilirsiniz. Hata ayıklama daha sonra ayarladığının tüm kesme noktalarını temizlemelidir.  
  
> [!WARNING]
> [ICorDebugCode3::GetReturnValueLiveOffset Yöntemi](icordebugcode3-getreturnvalueliveoffset-method.md) `ICorDebugILFrame3::GetReturnValueForILOffset` ve yöntemleri yalnızca başvuru türleri için iade değeri bilgileri almanızı sağlar. İade değeri bilgilerinin değer türlerinden (diğer bir şekilde) <xref:System.ValueType>alınması desteklenmez.  
  
 `ILOffset` Parametre tarafından belirtilen IL ofset bir işlev arama sitesinde olmalıdır ve hata ayıklama iCorDebugCode3 tarafından döndürülen yerli ofset bir kesme noktasında [ayarlanmalıdır::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL ofset için. Hata ayıklama belirtilen IL ofset için doğru konumda durdurulmazsa, API başarısız olur.  
  
 İşlev çağrısı bir değer döndürmezse, API başarısız olur.  
  
 Bu `ICorDebugILFrame3::GetReturnValueForILOffset` yöntem yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetReturnValueLiveOffset Yöntemi](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 Arabirimi](icordebugilframe3-interface.md)
