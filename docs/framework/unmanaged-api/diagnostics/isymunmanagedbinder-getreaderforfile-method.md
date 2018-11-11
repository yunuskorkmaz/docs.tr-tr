---
title: ISymUnmanagedBinder::GetReaderForFile Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982821"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile Metodu
Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.  
  
 Bu yöntem, yalnızca yürütülebilir dosyanın yanındaki ise program veritabanı (PDB) dosyası açılır. Güvenlik nedeniyle bu değişiklik yapılmıştır. PDB dosyası için daha kapsamlı bir arama ihtiyacınız varsa, [Isymunmanagedbinder2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  
 `importer`  
 [in] Meta veri alma arayüzü işaretçisi.  
  
 `fileName`  
 [in] Dosya adı için bir işaretçi.  
  
 `searchPath`  
 [in] Arama yolu için bir işaretçi.  
  
 `pRetVal`  
 [out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedBinder Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [GetReaderForFile2 Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
