---
title: IMetaDataDispenserEx Arabirimi
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx Arabirimi
Genişletir [Imetadatadispenser arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) API meta verileri geçerli meta veri kapsamına nasıl çalıştığını denetleyen yeteneği sağlamak için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindAssembly Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Bu yöntem uygulanmadı. Adlı E_NOTIMPL döndürür.|  
|[FindAssemblyModule Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Bu yöntem uygulanmadı. Adlı E_NOTIMPL döndürür.|  
|[GetCORSystemDirectory Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Geçerli ortak dil çalışma zamanı (CLR) tutan dizinin alır. Bu yöntem yalnızca kullanım için işlem dışı hata ayıklayıcıları tarafından desteklenir. Başka bir bileşen tarafından çağrılan olursa E_NOTIMPL döndürür.|  
|[GetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Geçerli meta veri kapsam için belirtilen seçenek değerini alır. Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.|  
|[OpenScopeOnITypeInfo Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Bu yöntem uygulanmadı. Adlı E_NOTIMPL döndürür.|  
|[SetOption Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Belirtilen seçenek geçerli meta veri kapsam için belirli bir değeri ayarlar. Seçeneği geçerli bir meta veri kapsama çağrıları işlenme denetler.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
