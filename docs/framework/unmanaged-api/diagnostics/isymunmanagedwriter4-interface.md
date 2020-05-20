---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609475"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 Arabirimi
ISymUnmanagedWriter4 arabirimi.  
  
## <a name="syntax"></a>Söz dizimi  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDebugInfoWithPadding Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` . Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .<br /><br /> Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 Arabirimi](isymunmanagedwriter3-interface.md)
