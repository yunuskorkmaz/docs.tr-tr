---
title: IMetaDataImport::GetRVA Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 58ab9ee9381fce4d7af1910df6c8d3bb813bcf13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490900"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA Metodu
Belirtilen belirteçle temsil edilen metodun veya alanın göreli sanal adresini (RVA) ve uygulama bayraklarını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 'ndaki İçin RVA 'yu döndürecek kod nesnesini temsil eden bir MethodDef veya FieldDef meta veri belirteci. Belirteç bir FieldDef ise, alan genel bir değişken olmalıdır.  
  
 `pulCodeRVA`  
 dışı Belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresine yönelik bir işaretçi.  
  
 `pdwImplFlags`  
 dışı Yöntemi için uygulama bayraklarının bir işaretçisi. Bu değer, [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırmasındaki bir bit dır. Değeri `pdwImplFlags` yalnızca `tk` bir MethodDef belirtecidir geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
