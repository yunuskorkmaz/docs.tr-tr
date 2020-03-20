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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178948"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset Metodu
Belirli bir IL ofset için, hata ayıklamanın bir işlevden geri dönüş değerini elde edilebilmek için kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.  
  
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
 IL ofset. Bir işlev arama sitesi olmalıdır veya işlev çağrısı başarısız olur.  
  
 `bufferSize`  
 Depolamak `pOffsets`için kullanılabilir bayt sayısı.  
  
 `pFetched`  
 Geri döndürülen uzaklık sayısına işaretçi. Genellikle değeri 1'dir, ancak tek bir IL `CALL` yönergesi birden çok montaj yönergesi ile eşlenebilir.  
  
 `pOffsets`  
 Bir dizi yerel uzaklık. Tipik olarak, tek bir IL yönergesi birden çok `CALL` derleme yönergesi için birden çok harita eşleyebilir rağmen, `pOffsets` tek bir ofset içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, başvuru türünü döndüren bir yöntemin geri dönüş değerini almak için [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemi ile birlikte kullanılır. Bir IŞLEV çağrı sitesine IL ofset'in bu yönteme geçirilmesi bir veya daha fazla yerel uzaklık döndürür. Hata ayıklama, işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilir. Hata ayıklayıcı kesme noktalarından birine ulaştığında, bu yönteme geçtiğiniz IL ofsetini iade değerini almak için [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemine geçirebilirsiniz. Hata ayıklama daha sonra ayarladığının tüm kesme noktalarını temizlemelidir.  
  
> [!WARNING]
> `ICorDebugCode3::GetReturnValueLiveOffset` Ve [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemleri yalnızca başvuru türleri için iade değeri bilgileri almanızı sağlar. İade değeri bilgilerinin değer türlerinden (diğer bir şekilde) <xref:System.ValueType>alınması desteklenmez.  
  
 İşlev aşağıdaki `HRESULT` tabloda gösterilen değerleri döndürür.  
  
|`HRESULT`Değer|Açıklama|  
|---------------------|-----------------|  
|`S_OK`|Başarılı.|  
|`CORDBG_E_INVALID_OPCODE`|Verilen IL ofset sitesi bir çağrı yönergesi değildir veya işlev döndürür. `void`|  
|`CORDBG_E_UNSUPPORTED`|Verilen IL ofset uygun bir çağrıdır, ancak iade türü iade değeri almak için desteklenmez.|  
  
 Bu `ICorDebugCode3::GetReturnValueLiveOffset` yöntem yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetReturnValueForILOffset Yöntemi](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 Arabirimi](icordebugcode3-interface.md)
