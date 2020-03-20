---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179405"
---
# <a name="getscope2-method"></a>GetScope2 Metodu
Bir alma kapsamı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Hedef montaj kimliği.  
  
 `FileToken`  
 Hangi dosyanın kimlik almak için.  
  
 `dwScope`  
 Almak için sıfır tabanlı kapsam.  
  
 `ppImportScope`  
 Belirtilen kapsam için [IMetaDataImport2 Arabirim](../metadata/imetadataimport2-interface.md) arabirimine işaretçisi alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 Alink.h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
