---
title: ICorDebugCode3::GetReturnValueLiveOffset Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c75db784a404298b86ed42692573a509ea56cf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415535"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset Metodu
Belirtilen bir IL uzaklığı, hata ayıklayıcı dönüş değeri bir işleve alabilmesi adına, bir kesme noktası nereye yerleştirileceğini yerel uzaklıkları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ILoffset`  
 IL uzaklığı. Bir işlev çağrısı site olmalı veya işlev çağrısı başarısız olur.  
  
 `bufferSize`  
 Depolamak kullanılabilir bayt sayısını `pOffsets`.  
  
 `pFetched`  
 Gerçekte döndürülen uzaklıkları sayısı için bir işaretçi. Genellikle, değer 1'dir, ancak tek bir IL yönergesi birden çok eşleyebilirsiniz `CALL` derleme yönergeleri.  
  
 `pOffsets`  
 Yerel uzaklıkları dizisi. Genellikle, `pOffsets` tek bir IL yönergesi birden çok eşlemek üzere birden çok eşleyebilirsiniz rağmen tek bir uzaklık içerir `CALL` derleme yönergeleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile birlikte kullanılan [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) bir başvuru türü döndüren bir yöntem dönüş değerini almak için yöntemi. Bu yöntemin bir işlev çağrısı siteye uzaklığı bir IL geçirme bir veya daha fazla yerel uzaklıklarını döndürür. Hata ayıklayıcı kesme noktaları bu yerel uzaklıkları işlevinde sonra ayarlayabilirsiniz. Hata ayıklayıcı kesme noktaları geldiğinde, bu yönteme geçirilen aynı IL uzaklığı sonra geçirebilirsiniz [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) dönüş değerini almak için yöntemi. Hata ayıklayıcı sonra ayarlayın kesme noktaları temizlemeniz gerekir.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` Ve [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemleri yalnızca başvuru türleri dönüş değeri bilgilerini edinin izin verir. Değer türlerinden dönüş değeri bilgileri alınıyor (diğer bir deyişle, türetilen tüm türleri <xref:System.ValueType>) desteklenmiyor.  
  
 İşlevi döndürür `HRESULT` aşağıdaki tabloda gösterilen değerleri.  
  
|`HRESULT` Değer|Açıklama|  
|---------------------|-----------------|  
|`S_OK`|Başarılı.|  
|`CORDBG_E_INVALID_OPCODE`|Verilen IL uzaklığı sitesini bir çağrı yönergesi değil ya da işlevi döndürür `void`.|  
|`CORDBG_E_UNSUPPORTED`|Verilen IL uzaklığı, uygun bir çağrı olmakla birlikte bir dönüş değeri almak için dönüş türü desteklenmiyor.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetReturnValueForILOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
