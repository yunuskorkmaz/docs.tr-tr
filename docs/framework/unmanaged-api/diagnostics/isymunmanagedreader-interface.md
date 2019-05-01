---
title: ISymUnmanagedReader Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986368"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader Arabirimi
Belgeler, yöntemler ve değişkenler bir sembol deposundaki erişim sağlayan bir sembol okuyucu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDocument Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Bir belgeyi bulur.|  
|[GetDocuments Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Sembol deposu içerisinde tanımlanan tüm belgelerin dizisini döndürür.|  
|[GetDocumentVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Belirtilen belge belirtilen sürümünü alır.|  
|[GetGlobalVariables Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Tüm genel değişkenler döndürür.|  
|[GetMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Token metody verilen sembol okuyucu yöntemi alır.|  
|[GetMethodByVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Bir sembol okuyucu yöntemi verilen token metody ve bir düzenleme ve kopyalama sürüm numarasını alır.|  
|[GetMethodFromDocumentPosition Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Bir belge belirtilen konumda bir kesme noktası içeren yöntemi döndürür.|  
|[GetMethodsFromDocumentPosition Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Yöntemler, her biri bir belge belirtilen konumda bir kesme noktası içeren bir dizisini döndürür.|  
|[GetMethodVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Yöntem sürümünü alır.|  
|[GetNamespaces Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Bu sembol deposundaki genel kapsamda tanımlanan ad alanları alır.|  
|[GetSymAttribute Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Özel bir öznitelik adı üzerinde temel alır.|  
|[GetSymbolStoreFileName Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Sembol deposundaki disk dosya adı sağlar.|  
|[GetUserEntryPoint Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.|  
|[GetVariables Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Bir yerel olmayan değişken adı ve üst verilen döndürür.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Bu okuyucu modülü dosya adının yanı sıra, ile ilişkili meta verileri alma arabirimiyle sembol okuyucu başlatır.|  
|[ReplaceSymbolStore Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Mevcut simge deposu delta sembol deposu ile değiştirir.|  
|[UpdateSymbolStore Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Mevcut simge deposu delta sembol deposu ile güncelleştirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
