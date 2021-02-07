---
description: 'Daha fazla bilgi edinin: ImportFile yöntemi'
title: ImportFile Metodu
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: 82c9c7de7cd739ee205dc3695ea651643d01ea3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718167"
---
# <a name="importfile-method"></a>ImportFile Metodu

Derlemeleri ve ilişkisiz modülleri içeri aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszFilename`  
 İçeri aktarılacak dosyanın tam adı.  
  
 `pszTargetName`  
 Derlemeye bağlı olduğundan dosyayı yeniden adlandırmak için kullanılabilecek, isteğe bağlı çıkış dosyası adı.  
  
 `fSmartImport`  
 TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.  
  
 `pImportToken`  
 Benzersiz bir dosya KIMLIĞININ depolanacağı belirteç işaretçisi. Dosya bir derleme veya bir dosya olabilir.  
  
 `ppAssemblyScope`  
 [IMetaDataAssemblyImport arabirimine](../metadata/imetadataassemblyimport-interface.md)yönelik bir işaretçi alır. Dosya bir derleme değilse NULL olabilir.  
  
 `pdwCountOfScopes`  
 İçeri aktarılan dosya ve/veya kapsamların sayısına yönelik işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
