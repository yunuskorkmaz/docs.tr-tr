---
title: IMetaDataDispenser::OpenScopeOnMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175934"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory Yöntemi
Varolan meta verileri içeren bir bellek alanı açar. Diğer bir deyişle, bu yöntem, varolan verilerin meta veri olarak kabul edildiği belirli bir bellek alanını açar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pData`  
 [içinde] Bellek alanının başlangıç adresini belirten bir işaretçi.  
  
 `cbData`  
 [içinde] Bellek alanının boyutu, baytlar halinde.  
  
 `dwOpenFlags`  
 [içinde] Açılış kipini (okuma, yazma vb.) belirtmek için [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasının değeri.  
  
 `riid`  
 [içinde] Döndürülecek istenilen meta veri arabiriminin IID'si; arayan, meta verileri almak (okumak) veya yayacak (yazmak) için arabirimi kullanır.  
  
 Değeri "içe aktarma" veya "yayış" arabirimlerinden birini `riid` belirtmelidir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [çıkış] Döndürülen arabirimin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta verilerin bellek içi kopyası ,"alma" arabirimlerinden birinden yöntemler kullanılarak sorgulanabilir veya "yaslamak" arabirimlerinden yöntemler kullanılarak sorgulanabilir.  
  
 `OpenScopeOnMemory` Yöntem, [iMetaDataDispenser'a benzer::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, ilgi meta verilerinin diskteki bir dosya yerine bellekte zaten var olması dışında.  
  
 Bellek hedef alanı ortak dil çalışma zamanı (CLR) meta `OpenScopeOnMemory` verileri içermiyorsa, yöntem başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
