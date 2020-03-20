---
title: IMetaDataAssemblyEmit::DefineExportedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177874"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType Yöntemi
Belirtilen dışa aktarılan tür için meta veri içeren bir `ExportedType` yapı oluşturur ve ilişkili meta veri belirteci döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szName`  
 [içinde] Dışa aktarılacak türün adı. Ortak dil çalışma zamanının sürüm 1.1 sürümü için, dışa aktarılan türün `TypeDef` adı, tür için verilen adla tam olarak eşleşmelidir.  
  
 `tkImplementation`  
 [içinde] Dışa aktarılan türün nerede uygulandığını belirten bir belirteç. Geçerli değerler ve bunlara bağlı anlamları şunlardır:  
  
- `mdFile`Tür, bu derleme içinde farklı bir dosyada uygulanır.  
  
- `mdAssemblyRef`Tür farklı bir derlemede uygulanır.  
  
- `mdExportedTYpe`Tür başka bir tür içinde iç içe.  
  
- `mdFileNil`Tür, bildirimle aynı dosyadadır ve iç içe geçen bir tür değildir.  
  
 `tkTypeDef`  
 [içinde] Dışa aktarılacak türü belirten meta verilerin belirteci. Bu değer, türü `TypeDef` uygulayan dosyadaki tabloya girilir ve yalnızca bu dosya bu derlemedeyse alakalıdır.  
  
 `dwExportedTypeFlags`  
 [içinde] Dışa aktarılan türiçin özellik ayarlarını tanımlayan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırma değerlerinin bitwise kombinasyonu.  
  
 `pmdct`  
 [çıkış] Dışa aktarılan türü gösteren döndürülen meta veri belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `ExportedType` derleme tarafından maruz kalan ve manifestoyu içeren bir modül dışında bir modülde uygulanan her tür için bir meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
