---
title: SetAssemblyFile2 Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 131f5d951e524ef48f2cfe1e3e88ef80ac21c452
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703687"
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 Yöntemi

Yeni bir derleme için adını ve seçeneklerini ayarlar. İlişkisiz modüller üretmeniz durumunda bu yöntemi çağırmayın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `pszFilename`  
 Bildirim dosyasının adı.  
  
 `pEmitter`  
 Bu dosya için [IMetaDataEmit2 arabirimi](../metadata/imetadataemit2-interface.md) arabirimi.  
  
 `afFlags`  
 [AssemblyFlags numaralandırması](../metadata/assemblyflags-enumeration.md)tarafından temsil edilen seçenekler.  
  
 `pAssemblyID`  
 Oluşturulan derlemenin benzersiz KIMLIĞINI alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
