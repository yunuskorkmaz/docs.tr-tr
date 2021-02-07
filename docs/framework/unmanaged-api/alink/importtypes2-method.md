---
description: 'Daha fazla bilgi edinin: ImportTypes2 yöntemi'
title: ImportTypes2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: ca0d174061608f9b4abf524c43023e867e9a9646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662617"
---
# <a name="importtypes2-method"></a>ImportTypes2 Yöntemi

Türlerin içeri aktarımını başlatır. [ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türleri içeri aktarmaya başlamak için bu yöntemi çağırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 İçeri aktarılacak derleme KIMLIĞI.  
  
 `FileToken`  
 İçinden içeri aktarılacak dosyanın KIMLIĞI.  
  
 `dwScope`  
 İçinden içeri aktarılacak sıfır tabanlı kapsam.  
  
 `phEnum`  
 Verilen kapsamdaki türler için numaralandırıcı tanıtıcısını alır.  
  
 `ppImportScope`  
 İsteğe bağlı olarak [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) arabirimini alır.  
  
 `pdwCountOfTypes`  
 İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
