---
title: ICorDebugProcess6::GetExportStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 118f52db63464b4c9355ba9ee7f330b996c5bf71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792241"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo Metodu
Yönetilen kodda adım adım yardım için çalışma zamanına aktarılmış işlevler hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametreler  
 pszExportName  
 'ndaki PE dışarı aktarma tablosunda yazıldığı şekilde bir çalışma zamanı dışa aktarma işlevinin adı.  
  
 invokeKind  
 dışı İçe aktarılmış işlevin yönetilen kodu nasıl çağıracağına ilişkin [cordebugcodeınvokekind](cordebugcodeinvokekind-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.  
  
 ınvokeamaç  
 dışı İçe aktarılmış işlevin neden yönetilen kodu çağıradığına ilişkin bir [Cordebugcodeınvokeamaç](cordebugcodeinvokepurpose-enumeration.md) numaralandırması üyesine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.  
  
|Dönüş değeri|Açıklama|  
|------------------|-----------------|  
|`S_OK`|Yöntem çağrısı başarılı oldu.|  
|`E_POINTER`|`pInvokeKind` veya `pInvokePurpose` **null**.|  
|Başarısız olan diğer `HRESULT` değerleri.|Uygun şekilde.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
