---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedciltçi:: GetReaderForFile yöntemi'
title: ISymUnmanagedBinder::GetReaderForFile Yöntemi
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
ms.openlocfilehash: ede494cbc1bbe4059b98a639c1d0621dc2cbdfa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790223"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile Yöntemi

Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.  
  
 Bu yöntem, program veritabanı (PDB) dosyasını yalnızca yürütülebilir dosyanın yanında olduğunda açar. Bu değişiklik güvenlik amacıyla yapılmıştır. PDB dosyası için daha kapsamlı bir aramanız gerekiyorsa, [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametreler  

 `importer`  
 'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.  
  
 `fileName`  
 'ndaki Dosya adı işaretçisi.  
  
 `searchPath`  
 'ndaki Arama yoluna yönelik bir işaretçi.  
  
 `pRetVal`  
 dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedBinder Arabirimi](isymunmanagedbinder-interface.md)
- [GetReaderForFile2 Yöntemi](isymunmanagedbinder2-getreaderforfile2-method.md)
