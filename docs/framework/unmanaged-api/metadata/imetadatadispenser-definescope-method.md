---
title: IMetaDataDispenser::DefineScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1763f9341af2d90cf465cb554bf7f282a4d92058
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777803"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope Yöntemi
Yeni meta verileri oluşturma bellekte yeni bir alan oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `rclsid`  
 [in] Oluşturulacak CLSID meta veri yapıları sürümü. Bu değer, .NET Framework sürüm 2.0 için CLSID_CorMetaDataRuntime olmalıdır.  
  
 `dwCreateFlags`  
 [in] Seçeneklerini belirten bayraklar. Bu değer, .NET Framework 2.0 için sıfır olmalıdır.  
  
 `riid`  
 [in] Döndürülecek istenen meta veri arayüzü Laboratuvardaki; çağıran, yeni meta verileri oluşturmak için arabirim kullanır.  
  
 Değerini `riid` "Yayımla" arabirimlerinden birini belirtmeniz gerekir. IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2 değerler geçerlidir.  
  
 `ppIUnk`  
 [out] Döndürülen arabirim işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineScope` bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz GUID (modülü sürüm tanımlayıcısı veya MVID) oluşturur ve yayılan derleme birimini modülü tablosunda bir giriş oluşturur.  
  
 Kullanarak bir bütün olarak meta veri kapsama öznitelikler ekleyebilirsiniz [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) veya [Imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) , uygun şekilde yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
