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
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432075"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType Yöntemi
Belirtilen içe aktarılmış tür için meta verileri içeren bir `ExportedType` yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
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
 'ndaki Aktarılacak türün adı. Ortak dil çalışma zamanının 1,1 sürümü için, verilen türün adı tür için `TypeDef` verilen adla tam olarak eşleşmelidir.  
  
 `tkImplementation`  
 'ndaki İçe aktarılmış türün nerede uygulandığını belirten bir belirteç. Geçerli değerler ve bunlarla ilişkili anlamları şunlardır:  
  
- `mdFile` bu derleme içindeki farklı bir dosyada uygulandı.  
  
- `mdAssemblyRef` türü farklı bir derlemede uygulandı.  
  
- tür başka bir tür içinde iç içe `mdExportedTYpe`.  
  
- `mdFileNil` türü bildirimle aynı dosyada ve iç içe geçmiş bir tür değil.  
  
 `tkTypeDef`  
 'ndaki Meta veriye aktarılacak türü belirten bir belirteç. Bu değer, türü uygulayan dosyadaki `TypeDef` tablosuna girilir ve yalnızca bu dosya bu derlemede olduğunda ilgilidir.  
  
 `dwExportedTypeFlags`  
 'ndaki İçe aktarılmış tür için özellik ayarlarını tanımlayan [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
 `pmdct`  
 dışı Verilen türü gösteren döndürülen meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu derleme tarafından sunulan ve bildirimi içeren bir modülde uygulanan her tür için bir `ExportedType` meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
