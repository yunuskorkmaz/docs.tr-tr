---
title: ISymUnmanagedReader Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56e0012ae1412c0fb5b434d3b4c0221831296c60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader Arabirimi
Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDocument yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Bir belge bulur.|  
|[GetDocuments yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.|  
|[GetDocumentVersion yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Belirtilen belge belirtilen sürümünü alır.|  
|[GetGlobalVariables yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Tüm genel değişkenler döndürür.|  
|[GetMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Bir simge okuyucu yöntemi bir yöntem belirteci verilen alır.|  
|[GetMethodByVersion yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Bir simge okuyucu yöntemi, verilen bir yöntem belirteci ve düzenleme ve kopyalama sürüm numarasını alır.|  
|[GetMethodFromDocumentPosition yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.|  
|[GetMethodsFromDocumentPosition yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.|  
|[GetMethodVersion yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Yöntem sürümünü alır.|  
|[GetNamespaces yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Bu simge deposundaki genel kapsamda tanımlanan ad alanları alır.|  
|[GetSymAttribute yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Adını dayalı özel bir öznitelik alır.|  
|[GetSymbolStoreFileName yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Sembol deposu disk üzerinde dosya adı sağlar.|  
|[GetUserEntryPoint yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.|  
|[GetVariables yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.|  
|[Initialize yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.|  
|[ReplaceSymbolStore yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Varolan sembol deposu delta sembol deposu ile değiştirir.|  
|[UpdateSymbolStore yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Varolan sembol deposu delta sembol deposu ile güncelleştirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama sembol deposu arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Isymunmanagedreader2 arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
