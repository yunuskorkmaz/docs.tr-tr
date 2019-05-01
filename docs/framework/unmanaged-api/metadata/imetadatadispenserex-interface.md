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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992608"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx Arabirimi
Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen olanağı sağlamak için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindAssembly Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Bu yöntem uygulanmadı. Çağrılırsa E_NOTIMPL döndürür.|  
|[FindAssemblyModule Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Bu yöntem uygulanmadı. Çağrılırsa E_NOTIMPL döndürür.|  
|[GetCORSystemDirectory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Geçerli ortak dil çalışma zamanının (CLR) tutan dizinin alır. Bu yöntemi kullanmak için yalnızca işlem dışı hata ayıklayıcıları tarafından desteklenir. Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.|  
|[GetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Geçerli meta veri kapsam için belirtilen seçenek değerini alır. Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.|  
|[OpenScopeOnITypeInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Bu yöntem uygulanmadı. Çağrılırsa E_NOTIMPL döndürür.|  
|[SetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Belirtilen seçeneği geçerli meta veri kapsam için belirli bir değere ayarlar. Geçerli bir meta veri kapsama çağrıları nasıl işleneceğini seçeneği denetler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
