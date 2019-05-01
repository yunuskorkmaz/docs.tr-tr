---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962345"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 Arabirimi
Isymunmanagedwriter4 arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirimi aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDebugInfoWithPadding Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Aynı şekilde işler [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verileri yapmak için bir sonlandırıcı null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`. Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen küçüktür `MAX_PATH`.<br /><br /> Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
