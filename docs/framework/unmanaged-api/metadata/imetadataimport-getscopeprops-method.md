---
description: ': IMetaDataImport:: GetScopeProps yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetScopeProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789157"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps Metodu

Geçerli meta veri kapsamındaki derleme ya da modülün adını ve isteğe bağlı olarak sürüm tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szName`  
 dışı Derleme veya modül adı için bir arabellek.  
  
 `cchName`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szName` .  
  
 `pchName`  
 dışı İçinde döndürülen geniş karakter sayısı `szName` .  
  
 `pmvid`  
 [Out, isteğe bağlı] Derlemenin veya modülün sürümünü benzersiz bir şekilde tanımlayan GUID işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu özellikleri ayarlamak için [ımetadatayayma:: SetModuleProps](imetadataemit-setmoduleprops-method.md) yöntemi kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
