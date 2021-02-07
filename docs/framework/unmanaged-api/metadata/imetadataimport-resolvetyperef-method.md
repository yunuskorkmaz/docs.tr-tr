---
description: ': IMetaDataImport:: ResolveTypeRef yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0634bac77f457432948d0c2887d676e95430d05d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677569"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef Yöntemi

<xref:System.Type>Belirtilen TypeRef belirteci ile temsil edilen bir başvuruyu çözümler.  
  
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
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
