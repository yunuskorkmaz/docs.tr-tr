---
title: IMetaDataDispenserEx Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431151"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx Arabirimi
Meta veri API 'Lerinin geçerli meta veri kapsamında nasıl çalıştığını denetleme yeteneğini sağlamak için [ımetadatadağıtıcı arabirim](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindAssembly Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[FindAssemblyModule Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[GetCORSystemDirectory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır. Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir. Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.|  
|[GetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.|  
|[OpenScopeOnITypeInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[SetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
