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
ms.openlocfilehash: f55c8986d2efc78b6fcd2840bad588af84228017
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561784"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu
Yöntemler, her biri bir belge belirtilen konumda bir kesme noktası içeren bir dizisini döndürür.  
  
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
 [in] Belirtilen belge satır.  
  
 `column`  
 [in] Belirtilen belgeyi içeren sütun.  
  
 `cMethod`  
 [in] Boyutu `pRetVal` dizisi.  
  
 `pcMethod`  
 [out] Döndürülen öğe sayısını alır bir değişken işaretçisi `pRetVal` dizisi.  
  
 `pRetVal`  
 [out] Bir dizi işaretçileri, her biri için işaret eden bir [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme noktası içeren bir yöntemi temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ISymUnmanagedReader Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
