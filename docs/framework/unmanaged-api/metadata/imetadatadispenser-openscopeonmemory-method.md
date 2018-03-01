---
title: "IMetaDataDispenser::OpenScopeOnMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d206863736387df04157ed752a6269b22a884b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory Yöntemi
Var olan meta veriler içeren bellek alanı açılır. Diğer bir deyişle, bu yöntem belirtilen alan var olan verileri meta verileri kabul edilir bellek açar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pData`  
 [in] Bellek alanının başlangıç adresini belirtir işaretçi.  
  
 `cbData`  
 [in] Bellek alanının bayt cinsinden boyutu.  
  
 `dwOpenFlags`  
 [in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması (okuma, yazma ve benzeri) modunu açmak için belirtin.  
  
 `riid`  
 [in] Döndürülecek istenen meta veri arabirimi IID; Arayan (okuma) almak veya (yazma) meta veri yayma arabirimini kullanır.  
  
 Değeri `riid` "Al" veya "Yayımla" arabirimleri birini belirtmeniz gerekir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 arasındadır.  
  
 `ppIUnk`  
 [out] Döndürülen arabirimi yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek içi kopya meta verilerin "alma" arabirimleri birinden yöntemleri kullanarak ya da "Yayımla" arabirimleri birinden yöntemleri kullanarak eklenen sorgulanabilir.  
  
 `OpenScopeOnMemory` Yöntemi benzer [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi, meta verileri ilgi bellek yerine disk üzerindeki bir dosya zaten var ancak bu.  
  
 Hedef alan bellek ortak dil çalışma zamanı (CLR) meta verileri, içermiyorsa `OpenScopeOnMemory` yöntemi başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
