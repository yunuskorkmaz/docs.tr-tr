---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178526"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo Metodu
Yönetilen kod üzerinden adım yardımcı olmak için çalışma zamanı dışa aktarılan işlevler hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametreler  
 pszExportName  
 [içinde] PE dışa aktarma tablosunda yazıldığı gibi bir çalışma zamanı dışa aktarma işlevinin adı.  
  
 ınvokekınd  
 [çıkış] Dışa aktarılan işlevin yönetilen kodu nasıl çağıracağını açıklayan [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) numaralandırmasının bir üyesine işaretçi.  
  
 invokeAmaç  
 [çıkış] Dışa aktarılan işlevin neden yönetilen kodu arayacağını açıklayan [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) numaralandırmasının bir üyesine işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem, aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Döndürülen değer|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Yöntem çağrısı başarılı oldu.|  
|`E_POINTER`|`pInvokeKind`veya `pInvokePurpose` **null**olduğunu .|  
|Diğer `HRESULT` başarısız değerler.|Uygun olduğu kadar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
