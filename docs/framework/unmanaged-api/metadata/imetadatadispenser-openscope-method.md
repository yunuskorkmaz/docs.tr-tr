---
title: IMetaDataDispenser::OpenScope Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175947"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope Yöntemi
Varolan, diskteki bir dosyayı açar ve meta verilerini belleğe eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szScope`  
 [içinde] Açılacak dosyanın adı. Dosya ortak dil çalışma zamanı (CLR) meta verileri içermelidir.  
  
 `dwOpenFlags`  
 [içinde] Açılış kipini (okuma, yazma vb.) belirtmek için [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasının değeri.  
  
 `riid`  
 [içinde] Döndürülecek istenilen meta veri arabiriminin IID'si; arayan, meta verileri almak (okumak) veya yayacak (yazmak) için arabirimi kullanır.  
  
 Değeri "içe aktarma" veya "yayış" arabirimlerinden birini `riid` belirtmelidir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [çıkış] Döndürülen arabirimin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta verilerin bellek içi kopyası ,"alma" arabirimlerinden birinden yöntemler kullanılarak sorgulanabilir veya "yaslamak" arabirimlerinden yöntemler kullanılarak sorgulanabilir.  
  
 Hedef dosya CLR meta verileri içermiyorsa, `OpenScope` yöntem başarısız olur.  
  
 .NET Framework sürüm 1.0 ve sürüm 1.1'de, `dwOpenFlags` ofRead'e ayarlı bir kapsam açılırsa, paylaşım için uygundur. Diğer bir deyişle, `OpenScope` daha önce açılmış bir dosyanın adına sonraki çağrıları geçmek için, varolan kapsam yeniden kullanılır ve yeni bir veri yapıları kümesi oluşturulmaz. Ancak, sorunlar bu paylaşım nedeniyle ortaya çıkabilir.  
  
 .NET Framework sürüm 2.0'da, `dwOpenFlags` ofRead'e ayarlı olarak açılan kapsamlar artık paylaşılmaz. Kapsamın paylaşılmasına izin vermek için ReadOnly değerini kullanın. Kapsam paylaşıldığında, "okuma/yazma" meta veri arabirimleri kullanan sorgular başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
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
