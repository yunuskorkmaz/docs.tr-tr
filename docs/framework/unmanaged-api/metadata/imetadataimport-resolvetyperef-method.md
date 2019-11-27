---
title: IMetaDataImport::ResolveTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431477"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi
Belirtilen TypeRef belirteci ile temsil edilen bir <xref:System.Type> başvurusunu çözümler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tr`  
 'ndaki İçin başvurulan tür bilgilerini döndürecek olan TypeRef meta veri belirteci.  
  
 `riid`  
 'ndaki `ppIScope`döndürülecek arabirimin IID 'si. Genellikle bu IID_IMetaDataImport olacaktır.  
  
 `ppIScope`  
 dışı Başvurulan türün tanımlandığı modül kapsamına yönelik arabirim.  
  
 `ptd`  
 dışı Başvurulan türü temsil eden bir TypeDef belirtecinin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Birden çok uygulama etki alanı yüklenmişse bu yöntemi kullanmayın. Yöntem, uygulama etki alanı sınırlarına uymaz. Bir derlemenin birden çok sürümü yüklüyse ve aynı ad alanıyla aynı türü içeriyorsa, yöntemi bulduğu ilk türün modül kapsamını döndürür.  
  
 `ResolveTypeRef` yöntemi, diğer modüllerde tür tanımını arar. Tür tanımı bulunursa `ResolveTypeRef`, bu modül kapsamına bir arabirim ve tür için de TypeDef belirtecini döndürür.  
  
 Çözümlenecek tür başvurusunda AssemblyRef 'nin bir çözüm kapsamı varsa `ResolveTypeRef` yöntemi, yalnızca [ımetadatadağıtıcı:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) yöntemi veya [ımetadatadağıtıcı:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoduna yapılan çağrılarla zaten açılmış olan meta veri kapsamlarındaki eşleşmeyi arar. Bunun nedeni `ResolveTypeRef` yalnızca diskte veya derlemenin depolandığı genel derleme önbelleğinde bulunan AssemblyRef kapsamından saptanamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
