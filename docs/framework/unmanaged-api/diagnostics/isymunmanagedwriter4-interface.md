---
title: ISymUnmanagedWriter4 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 Arabirimi
Isymunmanagedwriter4 arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim, aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDebugInfoWithPadding Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Aynı işlevleri [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verilerini yapmak için bir sonlandırma null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`. Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen değerinden `MAX_PATH`.<br /><br /> Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter3 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
