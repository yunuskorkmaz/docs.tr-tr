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
ms.openlocfilehash: 11382f00839917185ba3c85b8fbae5c32d0b0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448616"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope Yöntemi
Yeni bir alan yeni meta oluşturabileceğiniz bellekte oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rclsid`  
 [in] Oluşturulacak CLSID meta veri yapılarını sürümünün. Bu değer .NET Framework sürüm 2.0 için CLSID_CorMetaDataRuntime olmalıdır.  
  
 `dwCreateFlags`  
 [in] Seçeneklerini belirtin bayraklar. Bu değer, .NET Framework 2.0 için sıfır olmalıdır.  
  
 `riid`  
 [in] Döndürülecek istenen meta veri arabirimi IID; çağıran ve yeni meta oluşturmak için arabirimini kullanır.  
  
 Değeri `riid` "Yayımla" arabirimleri birini belirtmeniz gerekir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2 değerleridir.  
  
 `ppIUnk`  
 [out] Döndürülen arabirimi yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineScope` bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz GUID (Modül sürümü tanıtıcısı veya MVID) oluşturur ve gösterilmesini derleme birimini modülü tablosunda bir giriş oluşturur.  
  
 Kullanarak bir bütün olarak meta veri kapsama öznitelikler ekleyebilirsiniz [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) veya [Imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) uygun şekilde yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataDispenser Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
