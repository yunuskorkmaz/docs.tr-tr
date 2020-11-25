---
title: ImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 762f78900add70238971978ceecda089d0c725ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705117"
---
# <a name="importtypes-method"></a>ImportTypes Yöntemi

[ImportFile yöntemi](importfile-method.md)aracılığıyla içeri aktarılan her kapsamdan türlerin içeri aktarılmasını başlatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 İçeri aktarılacak derlemenin KIMLIĞI.  
  
 `FileToken`  
 İçeri aktarılacak dosyanın KIMLIĞI.  
  
 `dwScope`  
 İçeri aktarılacak sıfır tabanlı kapsam.  
  
 `phEnum`  
 Bu kapsamdaki türler için numaralandırıcı tanıtıcısını alır.  
  
 `ppImportScope`  
 İsteğe bağlı olarak [IMetaDataImport arabirim](../metadata/imetadataimport-interface.md) arabirimini alır.  
  
 `pdwCountOfTypes`  
 İsteğe bağlı olarak, belirtilen kapsamdaki türlerin sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
