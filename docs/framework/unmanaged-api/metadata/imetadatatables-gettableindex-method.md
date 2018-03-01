---
title: IMetaDataTables::GetTableIndex Metodu
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
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d2e51b9975748642d66e5b5104dc24936b4a7e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgettableindex-method"></a>IMetaDataTables::GetTableIndex Metodu
Belirtilen belirteç tarafından başvurulan tablo için dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `token`  
 [in] Bir tabloya başvuruyorsa belirteci.  
  
 `pixTbl`  
 [out] Başvurulan tablo için döndürülen dizin için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz. GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın. Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
