---
title: IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 152f62fddee3eaa7fa14e454e6eb7ea2547265ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731585"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a>IMetaDataAssemblyImport::FindManifestResourceByName Yöntemi

Belirtilen ada sahip bildirim kaynağına yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a>Parametreler  

 `szName`  
 'ndaki Kaynağın adı.  
  
 `ptkManifestResource`  
 dışı `mdManifestResource` Her biri bir bildirim kaynağını temsil eden meta veri belirteçlerini depolamak için kullanılan dizi.  
  
## <a name="remarks"></a>Açıklamalar  

 `FindManifestResourceByName`Yöntemi, başvuruları çözümlemek için ortak dil çalışma zamanı tarafından çalıştırılan standart kuralları kullanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../deployment/how-the-runtime-locates-assemblies.md)
