---
title: ISymUnmanagedBinder3 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157514"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 Arabirimi
Sembol bağlayıcı arabirimini genişletir. Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde `ISymUnmanagedBinder` arabirimi.  
  
> [!IMPORTANT]
>  Bu, güvenilmeyen bir kaynaktan bir program veritabanı (PDB) dosyası açmak için bir güvenlik riski oluşturur.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReaderFromCallback Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|Uygulama veya geri çağırma ya da kaynağı izin verir bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgileri almak için|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
