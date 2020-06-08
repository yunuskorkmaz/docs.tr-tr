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
ms.openlocfilehash: 12a32b5d2f0647ea2d9b696d08d6644e30be0c65
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501371"
---
# <a name="imetadatadispenserdefinescope-method"></a>IMetaDataDispenser::DefineScope Yöntemi
Bellekte yeni meta veri oluşturabileceğiniz yeni bir alan oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Oluşturulacak meta veri yapıları sürümünün CLSID değeri. Bu değer, .NET Framework sürüm 2,0 için CLSID_CorMetaDataRuntime olmalıdır.  
  
 `dwCreateFlags`  
 'ndaki Seçenekleri belirten bayraklar. Bu değer, .NET Framework 2,0 için sıfır olmalıdır.  
  
 `riid`  
 'ndaki Döndürülecek istenen meta veri arabiriminin IID 'si; çağıran, yeni meta verileri oluşturmak için arabirimini kullanır.  
  
 Değerinin `riid` "yayma" arabirimlerinden birini belirtmesi gerekir. Geçerli değerler IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit veya IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 dışı Döndürülen arabirime yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `DefineScope`bellek içi meta veri tabloları kümesi oluşturur, meta veriler için benzersiz bir GUID (Modül sürümü tanımlayıcısı veya MVıD) oluşturur ve yayılmakta olan derleme biriminin modül tablosunda bir giriş oluşturur.  
  
 [Imetadatayayma:: SetModuleProps](imetadataemit-setmoduleprops-method.md) veya [ımetadatayayma::D efineCustomAttribute](imetadataemit-definecustomattribute-method.md) metodunu uygun şekilde kullanarak bir bütün olarak meta veri kapsamına öznitelikler ekleyebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataDispenser Yöntemi](imetadatadispenser-interface.md)
- [IMetaDataDispenserEx Arabirimi](imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
