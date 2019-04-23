---
title: ISymUnmanagedDocument::GetURL Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b42bb72975fad4c1830a961f83d9e3065d055b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187466"
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL Yöntemi
Tekdüzen Kaynak Konum Belirleyicisi (URL)'için bu belgeyi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchUrl`  
 [in] Karakter cinsinden boyutu, `szURL` arabellek.  
  
 `pcchUrl`  
 [out] Bir işaretçi bir değişkene null sonlandırma dahil olmak üzere URL'yi boyutunu alır.  
  
 `szUrl`  
 [out] URL'sini içeren arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedDocument Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
