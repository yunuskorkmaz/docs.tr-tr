---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 21d6520aae1367368973da1692f6bca3aeb2c129
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493662"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 Arabirimi
ISymUnmanagedWriter4 arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Description|  
|------------|-----------------|  
|[GetDebugInfoWithPadding Yöntemi](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Dize verilerini sabit boyutlu hale getirmek için, bir yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür `MAX_PATH` . Yalnızca yol dize uzunluğu değerinden küçükse doldurma verilir `MAX_PATH` .<br /><br /> Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 Arabirimi](isymunmanagedwriter3-interface.md)
