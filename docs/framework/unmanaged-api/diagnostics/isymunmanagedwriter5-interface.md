---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter5 Interface'
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 0902385576e1eed17cea672b04858c7e3ef7add8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761635"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 Arabirimi

ISymUnmanagedWriter5 arabirimi.  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Yöntemler  

 Bu arabirim aşağıdaki yöntemleri içerir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın. Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.|  
|[MapTokenToSourceSpan Yöntemi](isymunmanagedwriter5-maptokentosourcespan-method.md)|Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.<br /><br /> [OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.|  
|[OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın. Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 Arabirimi](isymunmanagedwriter4-interface.md)
