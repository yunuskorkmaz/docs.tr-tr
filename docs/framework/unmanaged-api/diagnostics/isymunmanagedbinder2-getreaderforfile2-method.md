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
ms.openlocfilehash: cea8a322fab6ef76873e668c622ac63e3a3f2862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428231"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 Metodu
Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak arabirimi.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `importer`  
 [in] Meta veri alma arayüzü için bir işaretçi.  
  
 `fileName`  
 [in] Dosya adı için bir işaretçi.  
  
 `searchPath`  
 [in] Arama yolu için bir işaretçi.  
  
 `searchPolicy`  
 [in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) bir simge Okuyucu için arama yaparken kullanılacak ilkeyi belirtir numaralandırması.  
  
 `pRetVal`  
 [out] Ayarlanmış bir işaretçi döndürülen için <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin sürümü modülü yanındaki sağ dışındaki alanlarda PDB dosyası arayabilirsiniz. Arama İlkesi birleştirerek denetlenebilir [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` yürütülebilir dosyanın yanındaki ve bir simge sunucuda PDB arar ancak kayıt defterini sorgulayın veya yürütülebilir dosyanın yolunu kullanın. Varsa `searchPath` parametresi sağlanır, bu dizinlerin her zaman aranır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedBinder2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [GetReaderForFile Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
