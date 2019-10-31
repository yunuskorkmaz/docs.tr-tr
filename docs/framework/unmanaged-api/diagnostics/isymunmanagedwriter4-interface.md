---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: a656777461c50b5a1593917278eb54abda982dc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134561"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 Arabirimi
ISymUnmanagedWriter4 arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDebugInfoWithPadding Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Dize verilerini sabit bir `MAX_PATH`boyutuna getirmek için, yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür. Padding yalnızca yol dize uzunluğunun `MAX_PATH`' den küçük olması durumunda verilir.<br /><br /> Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
