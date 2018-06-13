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
ms.openlocfilehash: a78616ea1dccdf82c4e00d23d2ff630c98cb4e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431909"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader Arabirimi
Belgeler, yöntemleri ve sembol deposu değişkenler erişim sağlayan bir simge okuyucuyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDocument Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Bir belge bulur.|  
|[GetDocuments Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.|  
|[GetDocumentVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Belirtilen belge belirtilen sürümünü alır.|  
|[GetGlobalVariables Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Tüm genel değişkenler döndürür.|  
|[GetMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Bir simge okuyucu yöntemi bir yöntem belirteci verilen alır.|  
|[GetMethodByVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Bir simge okuyucu yöntemi, verilen bir yöntem belirteci ve düzenleme ve kopyalama sürüm numarasını alır.|  
|[GetMethodFromDocumentPosition Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.|  
|[GetMethodsFromDocumentPosition Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.|  
|[GetMethodVersion Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Yöntem sürümünü alır.|  
|[GetNamespaces Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Bu simge deposundaki genel kapsamda tanımlanan ad alanları alır.|  
|[GetSymAttribute Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Adını dayalı özel bir öznitelik alır.|  
|[GetSymbolStoreFileName Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Sembol deposu disk üzerinde dosya adı sağlar.|  
|[GetUserEntryPoint Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Modül için kullanıcı giriş noktası olarak belirtilen yöntem varsa döndürür.|  
|[GetVariables Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Bu okuyucu modülü dosya adı yanı sıra, ilişkili meta verileri alma arabirimi simgesi okuyucu başlatır.|  
|[ReplaceSymbolStore Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Varolan sembol deposu delta sembol deposu ile değiştirir.|  
|[UpdateSymbolStore Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Varolan sembol deposu delta sembol deposu ile güncelleştirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanılama Simge Deposu Arabirimleri](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
