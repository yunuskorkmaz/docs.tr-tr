---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatadağıtıserex arabirimi'
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
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753542"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx Arabirimi

Meta veri API 'Lerinin geçerli meta veri kapsamında nasıl çalıştığını denetleme yeteneğini sağlamak için [ımetadatadağıtıcı arabirim](imetadatadispenser-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FindAssembly Yöntemi](imetadatadispenserex-findassembly-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[FindAssemblyModule Yöntemi](imetadatadispenserex-findassemblymodule-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[GetCORSystemDirectory Yöntemi](imetadatadispenserex-getcorsystemdirectory-method.md)|Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır. Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir. Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.|  
|[GetOption Yöntemi](imetadatadispenserex-getoption-method.md)|Geçerli meta veri kapsamı için belirtilen seçeneğin değerini alır. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.|  
|[OpenScopeOnITypeInfo Yöntemi](imetadatadispenserex-openscopeonitypeinfo-method.md)|Bu yöntem uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.|  
|[SetOption Yöntemi](imetadatadispenserex-setoption-method.md)|Belirtilen seçeneği geçerli meta veri kapsamı için verilen bir değere ayarlar. Seçeneği, geçerli meta veri kapsamına yapılan çağrıların işlenme biçimini denetler.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataDispenser Arabirimi](imetadatadispenser-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
