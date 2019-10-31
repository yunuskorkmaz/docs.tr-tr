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
ms.openlocfilehash: c7419e5c3677b5679a0ca5c234463ae6e205b7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090369"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
Bir işlevin dönüş değerini kapsülleyen bir "ICorDebugValue" nesnesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ILOffset`  
 Il kayması. Açıklamalar bölümüne bakın.  
  
 `ppReturnValue`  
 Bir işlev çağrısının dönüş değeri hakkında bilgi sağlayan bir "ICorDebugValue" arabirim nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir yöntemin dönüş değerini almak için [ICorDebugCode3:: Getreturnvaluelivesapmayı](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi ile birlikte kullanılır. Aşağıdaki iki kod örneğinde olduğu gibi, dönüş değerleri yok sayılan Yöntemler söz konusu olduğunda özellikle yararlıdır. İlk örnek <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemini çağırır, ancak yöntemin dönüş değerini yoksayar.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 İkinci örnek, hata ayıklama sırasında çok daha yaygın bir sorunu gösterir. Yöntemi bir yöntem çağrısında bağımsız değişken olarak kullanıldığından, dönüş değeri yalnızca hata ayıklayıcı çağrılan yöntem boyunca adım adım erişilebilir. Çoğu durumda, özellikle çağrılan yöntem bir dış kitaplıkta tanımlandığında, bu mümkün değildir.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 [ICorDebugCode3:: Getreturnvalueliveuzaklık](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodunu bir işlev ÇAĞRıSı sitesine Il uzaklığına geçirirseniz, bir veya daha fazla yerel uzaklık döndürür. Hata ayıklayıcı daha sonra işlevdeki bu yerel kaydırmalar üzerinde kesme noktaları ayarlayabilir. Hata ayıklayıcı kesme noktalarından birine geçtiğinde, dönüş değerini almak için bu yönteme geçirdiğiniz Il sapmasını geçirebilirsiniz. Hata ayıklayıcı daha sonra, ayarlandığı tüm kesme noktalarını temizlemelidir.  
  
> [!WARNING]
> [ICorDebugCode3:: Getreturnvaluelivesapmasını yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanıza olanak sağlar. Değer türlerinden dönüş değeri bilgileri alma (yani, <xref:System.ValueType>türetilen tüm türler) desteklenmez.  
  
 `ILOffset` parametresi tarafından belirtilen Il uzaklığında bir işlev çağrı sitesinde olması gerekir ve hata ayıklanan, aynı Il kayması için [ICorDebugCode3:: Getreturnvaluelivesapmayı](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi tarafından döndürülen yerel uzaklığında ayarlanan bir kesme noktasında durdurulmalıdır. Hata ayıklanan, belirtilen Il uzaklığında doğru konumda durdurulmamışsa, API başarısız olur.  
  
 İşlev çağrısı bir değer döndürmezse, API başarısız olur.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemi yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetReturnValueLiveOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
