---
title: SetAssemblyFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 45eed17b91f70d4188d1d89fc91a41455f3e845b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732651"
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile Yöntemi

Oluşturulacak derlemenin adını atar. İlişkisiz modüller üretilirken kullanılamaz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszFilename`  
 Bildirim dosyasının tam adı.  
  
 `pEmitter`  
 [Imetadatayayma arabirim](../metadata/imetadataemit-interface.md) arabirimine yönelik işaretçi.  
  
 `afFlags`  
 [AssemblyFlags numaralandırmasında](../metadata/assemblyflags-enumeration.md)tanımlanan bayraklar.  
  
 `pAssemblyID`  
 Elde edilen derlemenin KIMLIĞI işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
