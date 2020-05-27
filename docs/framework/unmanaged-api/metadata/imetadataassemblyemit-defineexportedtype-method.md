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
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008165"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType Yöntemi
`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Aktarılacak türün adı. Ortak dil çalışma zamanının 1,1 sürümü için, verilen türün adı, türü için verilen adla tam olarak eşleşmelidir `TypeDef` .  
  
 `tkImplementation`  
 'ndaki İçe aktarılmış türün nerede uygulandığını belirten bir belirteç. Geçerli değerler ve bunlarla ilişkili anlamları şunlardır:  
  
- `mdFile`Bu derleme içindeki farklı bir dosyada tür uygulandı.  
  
- `mdAssemblyRef`Tür, farklı bir derlemede uygulanır.  
  
- `mdExportedTYpe`Tür başka bir tür içinde iç içe geçmiş.  
  
- `mdFileNil`Tür, bildirimle aynı dosyada ve iç içe geçmiş bir tür değil.  
  
 `tkTypeDef`  
 'ndaki Meta veriye aktarılacak türü belirten bir belirteç. Bu değer `TypeDef` , türü uygulayan dosyanın tablosuna girilir ve yalnızca söz konusu dosya bu derlemede olduğunda ilgilidir.  
  
 `dwExportedTypeFlags`  
 'ndaki İçe aktarılmış tür için özellik ayarlarını tanımlayan [CorTypeAttr](cortypeattr-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
 `pmdct`  
 dışı Verilen türü gösteren döndürülen meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ExportedType`Bu derleme tarafından sunulan ve bildirimi içeren bir modülde uygulanan her tür için bir meta veri yapısı tanımlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
