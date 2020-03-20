---
title: IMetaDataImport::FindMethod Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177258"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod Yöntemi
Belirtilen <xref:System.Type> tarafından eklenen ve belirtilen ad ve meta veri imzasına sahip yöntem için MethodDef belirteci için bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 [içinde] `mdTypeDef` Üyeyi aramak için içine alan tür (sınıf veya arabirim) için belirteç. Bu değer `mdTokenNil`ise, arama global bir işlev için yapılır.  
  
 `szName`  
 [içinde] Aranacak yöntemin adı.  
  
 `pvSigBlob`  
 [içinde] Yöntemin ikili meta veri imzasına işaretçi.  
  
 `cbSigBlob`  
 [içinde] `pvSigBlob`Baytboyutu.  
  
 `pmb`  
 [çıkış] Eşleşen MethodDef belirteci için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi çevreleyen sınıf ını veya arabirimini (`td``szName`), adını ( ),`pvSigBlob`ve isteğe bağlı olarak imzasını ( ) kullanarak belirtirsiniz. Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.  
  
 İmzalar belirli `FindMethod` bir kapsama bağlı olduğundan, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, çevreleyen sınıfı veya değer türünü tanımlayan bir belirteç katıştırabilir. Belirteç, yerel TypeDef tablosuna bir dizindir. Geçerli kapsam bağlamının dışında bir çalışma zamanı imzası oluşturamazsınız ve bu imzayı `FindMethod`giriş olarak kullanamazsınız.  
  
 `FindMethod`yalnızca sınıf veya arabirimde doğrudan tanımlanan yöntemleri bulur; kalıtsal yöntemler bulamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
