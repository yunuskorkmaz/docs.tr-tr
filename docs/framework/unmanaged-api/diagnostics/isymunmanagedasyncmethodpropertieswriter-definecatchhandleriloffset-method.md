---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129183"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.  
  
 Oluşturulan catch 'in Il kayması, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için hata ayıklayıcı tarafından kullanılır. Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Dönüş Değeri  
 `HRESULT`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
