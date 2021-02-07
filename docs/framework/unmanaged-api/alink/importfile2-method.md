---
description: 'Daha fazla bilgi edinin: ImportFile2 yöntemi'
title: ImportFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 98da8ecf4bfc19e52c5a92e6509f6af49afbdd5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718063"
---
# <a name="importfile2-method"></a>ImportFile2 Yöntemi

Derlemeleri ve ilişkisiz modülleri içeri aktarır. Bu yöntem [ImportFile yöntemine](importfile-method.md)benzer, ancak içeri aktarılan dosya diskte mevcut olmasa bile çalışıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszFilename`  
 İçeri aktarılacak dosyanın adı.  
  
 `pszTargetName`  
 Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.  
  
 `pAssemblyScopeIn`  
 İsteğe bağlı [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimi.  
  
 `fSmartImport`  
 TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.  
  
 `pImportToken`  
 Dosya veya derleme için KIMLIĞI alır.  
  
 `ppAssemblyScope`  
 [IMetaDataAssemblyImport arabirim](../metadata/imetadataassemblyimport-interface.md) arabirimini alır. Dosya derleme değilse NULL.  
  
 `pdwCountOfScopes`  
 İçeri aktarılan dosya ve/veya kapsamların bulunduğu yer sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
