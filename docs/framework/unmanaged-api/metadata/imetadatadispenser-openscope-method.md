---
title: "IMetaDataDispenser::OpenScope Yöntemi"
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
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f1dad7303d83ae550f54d9173a9f4359239091f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope Yöntemi
Var olan, disk üzerindeki bir dosyayı açar ve belleğe meta verilerini eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szScope`  
 [in] Açılması için dosyanın adı. Ortak dil çalışma zamanı (CLR) meta veri dosyası içermelidir.  
  
 `dwOpenFlags`  
 [in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması (okuma, yazma ve benzeri) modunu açmak için belirtin.  
  
 `riid`  
 [in] Döndürülecek istenen meta veri arabirimi IID; Arayan (okuma) almak veya (yazma) meta veri yayma arabirimini kullanır.  
  
 Değeri `riid` "Al" veya "Yayımla" arabirimleri birini belirtmeniz gerekir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 arasındadır.  
  
 `ppIUnk`  
 [out] Döndürülen arabirimi yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek içi kopya meta verilerin "alma" arabirimleri birinden yöntemleri kullanarak ya da "Yayımla" arabirimleri birinden yöntemleri kullanarak eklenen sorgulanabilir.  
  
 Hedef dosya CLR meta verileri, içermiyorsa `OpenScope` yöntemi başarısız olur.  
  
 .NET Framework sürüm 1.0 ve sürüm 1.1, kapsam, açıldığında ile `dwOpenFlags` ofRead için ayarlanırsa, bu paylaşım için uygundur. Diğer bir deyişle, sonraki varsa çağrılar `OpenScope` geçişi daha önce açıldı bir dosya adına, varolan bir kapsamın yeniden ve veri yapıları yeni bir dizi oluşturulmadı. Ancak, sorunlar, bu paylaşımı nedeniyle ortaya çıkabilir.  
  
 .NET Framework sürüm 2. 0'da, kapsamları açılmış `dwOpenFlags` ofRead kümesine artık paylaşılan. Paylaşılan kapsam izin vermek için ofReadOnly değeri kullanın. Bir kapsam paylaşıldığında, "meta veri arabirimleri okuma/yazma" kullanan sorguları başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
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
