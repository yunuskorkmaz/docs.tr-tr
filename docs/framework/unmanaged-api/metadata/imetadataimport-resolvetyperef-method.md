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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951874"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi
Belirtilen TypeRef <xref:System.Type> belirteci ile temsil edilen bir başvuruyu çözümler.  
  
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
 'ndaki Döndürülecek arabirimin IID 'si `ppIScope`. Genellikle bu IID_IMetaDataImport olacaktır.  
  
 `ppIScope`  
 dışı Başvurulan türün tanımlandığı modül kapsamına yönelik arabirim.  
  
 `ptd`  
 dışı Başvurulan türü temsil eden bir TypeDef belirtecinin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Birden çok uygulama etki alanı yüklenmişse bu yöntemi kullanmayın. Yöntem, uygulama etki alanı sınırlarına uymaz. Bir derlemenin birden çok sürümü yüklüyse ve aynı ad alanıyla aynı türü içeriyorsa, yöntemi bulduğu ilk türün modül kapsamını döndürür.  
  
 Yöntemi `ResolveTypeRef` , diğer modüllerde tür tanımını arar. Tür tanımı bulunursa, `ResolveTypeRef` bu modül kapsamına ve tür için typedef belirtecine bir arabirim döndürür.  
  
 Çözümlenecek tür başvurusunun, AssemblyRef 'nin bir çözüm kapsamı varsa, `ResolveTypeRef` yöntemi yalnızca [ımetadatadağıtıcı:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoduna veya [' ye yapılan çağrılarla zaten açılmış olan meta veri kapsamları içinde bir eşleşme arar. Imetadatadağıtıcı:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi. Bunun nedeni `ResolveTypeRef` , yalnızca diskte veya derlemenin depolandığı genel derleme önbelleğinde bulunan AssemblyRef kapsamından saptanamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** Cor. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
