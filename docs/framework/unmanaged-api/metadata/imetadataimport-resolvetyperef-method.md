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
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503451"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi
<xref:System.Type>Belirtilen TypeRef belirteci ile temsil edilen bir başvuruyu çözümler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Döndürülecek arabirimin IID 'si `ppIScope` . Genellikle bu IID_IMetaDataImport olacaktır.  
  
 `ppIScope`  
 dışı Başvurulan türün tanımlandığı modül kapsamına yönelik arabirim.  
  
 `ptd`  
 dışı Başvurulan türü temsil eden bir TypeDef belirtecinin işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Birden çok uygulama etki alanı yüklenmişse bu yöntemi kullanmayın. Yöntem, uygulama etki alanı sınırlarına uymaz. Bir derlemenin birden çok sürümü yüklüyse ve aynı ad alanıyla aynı türü içeriyorsa, yöntemi bulduğu ilk türün modül kapsamını döndürür.  
  
 `ResolveTypeRef`Yöntemi, diğer modüllerde tür tanımını arar. Tür tanımı bulunursa, `ResolveTypeRef` Bu modül kapsamına ve tür Için typedef belirtecine bir arabirim döndürür.  
  
 Çözümlenecek tür başvurusunun AssemblyRef bir çözüm kapsamı varsa, `ResolveTypeRef` yöntemi yalnızca [ımetadatadağıtıcı:: OpenScope](imetadatadispenser-openscope-method.md) yöntemi veya [ımetadatadağıtıcı:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) metoduna yapılan çağrılarla zaten açılmış olan meta veri kapsamlarındaki eşleşmeyi arar. Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya derlemenin depolandığı genel derleme önbelleğinde bulunan AssemblyRef kapsamından saptanamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
