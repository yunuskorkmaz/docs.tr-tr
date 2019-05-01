---
title: ISymUnmanagedBinder2::GetReaderForFile2 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed289b2776e8ac4a12969060cd16c6163ebed2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940055"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 Metodu
Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.  
  
 Bu yöntem program veritabanı (PDB) dosyası için daha kapsamlı bir arama sağlar [Isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
 `importer`  
 [in] Meta veri alma arayüzü işaretçisi.  
  
 `fileName`  
 [in] Dosya adı için bir işaretçi.  
  
 `searchPath`  
 [in] Arama yolu için bir işaretçi.  
  
 `searchPolicy`  
 [in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirten sabit listesi.  
  
 `pRetVal`  
 [out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi bu sürümü, modül yanındaki sağ dışındaki alanlarda PDB dosyası için arama yapabilirsiniz. Arama ilke birleştirerek denetlenebilir [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` pdb yürütülebilir dosyanın yanındaki ve bir sembol sunucusu üzerinde görünür ancak kayıt defterini sorgulayın veya yürütülebilir dosyanın yolunu kullanın. Varsa `searchPath` parametresi sağlanır, bu dizinlerin her zaman aranır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedBinder2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [GetReaderForFile Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
