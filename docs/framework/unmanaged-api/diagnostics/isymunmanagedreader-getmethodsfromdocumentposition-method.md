---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c84aceb0faabd879911e9595a7f3154065e2191
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426204"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu
Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `document`  
 [in] Belirtilen belge.  
  
 `line`  
 [in] Belirtilen belge satırı.  
  
 `column`  
 [in] Belirtilen belge sütun.  
  
 `cMethod`  
 [in] Boyutunu `pRetVal` dizi.  
  
 `pcMethod`  
 [out] Döndürülen öğe sayısını alır bir değişken için bir işaretçi `pRetVal` dizi.  
  
 `pRetVal`  
 [out] Her biri işaret işaretçileri, bir dizi bir [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme noktası içeren bir yöntemi temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
