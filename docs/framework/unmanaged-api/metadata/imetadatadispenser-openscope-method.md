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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e157c758b472ea89e21c1ed1ba8c17693c20a3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777796"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope Yöntemi
Var olan ve disk üzerindeki bir dosya açılır ve meta verileri belleğe eşler.  
  
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
 [in] Açılması için dosyanın adı. Dosyanın ortak dil çalışma zamanı (CLR) meta verileri içermelidir.  
  
 `dwOpenFlags`  
 [in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) açmak için (okuma, yazma ve benzeri) modunu belirtmek için sabit listesi.  
  
 `riid`  
 [in] Döndürülecek istenen meta veri arayüzü Laboratuvardaki; çağıran, (okuma) alma ya da (yazma) meta verileri yayma arabirimini kullanır.  
  
 Değerini `riid` "Al" veya "Yayımla" arabirimlerinden birini belirtmeniz gerekir. IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 veya IID_IMetaDataImport2 değerler geçerlidir.  
  
 `ppIUnk`  
 [out] Döndürülen arabirim işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bellek içi kopyayı meta verilerin yöntemleri "Al" arabirimlerinden birini kullanarak veya eklenen "Yayımla" arabirimleri birinden yöntemleri kullanarak sorgulanabilir.  
  
 Hedef dosyanın CLR meta veriler içermiyorsa `OpenScope` yöntemi başarısız olur.  
  
 .NET Framework sürüm 1.0 ve sürüm 1.1, bir kapsam ise açıldığında ile `dwOpenFlags` için ofRead ayarlanırsa, bunu paylaşmak için uygundur. Diğer bir deyişle, varsa sonraki çağrılar `OpenScope` oluşturdular. daha önce açıldı bir dosya, var olan kapsamı yeniden ve yeni bir veri yapılarını kümesi oluşturulmaz. Ancak, sorunlar, bu paylaşım nedeniyle ortaya çıkabilir.  
  
 .NET Framework sürüm 2. 0'da, kapsamları ile açılır. `dwOpenFlags` ofRead kümesine artık paylaşılır. Paylaşılan kapsam için ofReadOnly değeri kullanın. Bir kapsam paylaşıldığında "meta veri arabirimleri okuma/yazma" kullanan sorguları başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
