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
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125943"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset Metodu
Belirtilen IL uzaklığı için bir kesme noktası, hata ayıklayıcı bir işlevden dönüş değeri alabilmesi nereye yerleştirileceğini yerleşik uzaklıkları alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ILoffset`  
 IL uzaklığı. Bir işlev çağrısı sitesi olmalıdır veya işlev çağrısı başarısız olur.  
  
 `bufferSize`  
 Depolamak kullanılabilir bayt sayısı `pOffsets`.  
  
 `pFetched`  
 Gerçekte döndürülen uzaklık sayısına yönelik işaretçi. Genellikle değeri 1'dir, ancak tek bir IL yönergesinin birden çok eşleyebilirsiniz `CALL` derleme yönergeleri.  
  
 `pOffsets`  
 Yerel uzaklıklar dizisi. Genellikle, `pOffsets` tek IL yönergesi birden çok eşlemek üzere birden çok olsa da, tek bir uzaklık içerir `CALL` derleme yönergeleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile birlikte kullanılan [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) bir başvuru türü döndüren bir yöntemin dönüş değerini almak için yöntemi. Bir IL bu yönteme bir işlev çağrısı siteye uzaklığını geçirirken bir veya daha fazla yerel uzaklıklar verir. Hata ayıklayıcı, ardından işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilirsiniz. Hata ayıklayıcı kesme noktalarından birine ulaştığında, ardından için bu yönteme geçilen aynı IL uzaklığını geçirebilirsiniz [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) dönüş değeri almak için yöntemi. Ardından hata ayıklayıcıyı ayarladığı tüm kesme noktalarını temizlemeniz gerekir.  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset` Ve [Icordebugılframe3::getreturnvalueforıloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanıza olanak tanır. Değer türlerinden dönüş değeri bilgilerini alma (diğer bir deyişle, öğesinden türetilen tüm türler <xref:System.ValueType>) desteklenmiyor.  
  
 İşlev döndürür `HRESULT` aşağıdaki tabloda gösterilen değerler.  
  
|`HRESULT` Değer|Açıklama|  
|---------------------|-----------------|  
|`S_OK`|Başarılı.|  
|`CORDBG_E_INVALID_OPCODE`|Belirtilen IL uzaklık sitesi bir çağrı talimatı değildir veya işlev döndürür `void`.|  
|`CORDBG_E_UNSUPPORTED`|Belirtilen IL uzaklığı uygun bir çağrıdır, ancak bir dönüş değeri almak için dönüş türü desteklenmiyor.|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemlerinde.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetReturnValueForILOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
