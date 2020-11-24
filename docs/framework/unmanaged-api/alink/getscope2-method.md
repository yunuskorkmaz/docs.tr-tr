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
ms.openlocfilehash: e8c6fd7dca13afe7504e447caca9a217c8136c27
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684531"
---
# <a name="getscope2-method"></a>GetScope2 Metodu

İçeri aktarma kapsamı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Hedef derlemenin KIMLIĞI.  
  
 `FileToken`  
 İçinden içeri aktarılacak dosyanın KIMLIĞI.  
  
 `dwScope`  
 İçeri aktarılacak sıfır tabanlı kapsam.  
  
 `ppImportScope`  
 Belirtilen kapsam için [IMetaDataImport2 arabirimi](../metadata/imetadataimport2-interface.md) arabirimine yönelik bir işaretçi alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
