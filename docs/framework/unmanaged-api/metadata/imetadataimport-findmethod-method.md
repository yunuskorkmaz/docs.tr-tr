---
description: ': IMetaDataImport:: FindMethod yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0d2866554fcb4dcf3984310e4da24d501f1fc7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803561"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod Yöntemi

Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan yöntemi Için MethodDef belirtecine yönelik bir işaretçi alır.  
  
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
 'ndaki `mdTypeDef` Aramak için üyeyi kapsayan türün belirteci (bir sınıf veya arabirim). Bu değer ise `mdTokenNil` , genel bir işlev için arama yapılır.  
  
 `szName`  
 'ndaki Aranacak yöntemin adı.  
  
 `pvSigBlob`  
 'ndaki Metodun ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki Bayt cinsinden boyut `pvSigBlob` .  
  
 `pmb`  
 dışı Eşleşen MethodDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Yöntemi kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` . Bir sınıfta veya arabirimde aynı ada sahip birden çok yöntem olabilir. Bu durumda, benzersiz eşleşmeyi bulmak için yöntemin imzasını geçirin.  
  
 `FindMethod`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. Belirteç, yerel TypeDef tablosunun bir dizinidir. Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı girişi yapılacak girdi olarak kullanabilirsiniz `FindMethod` .  
  
 `FindMethod` yalnızca sınıfta veya arabirimde doğrudan tanımlanmış yöntemleri bulur; devralınan yöntemleri bulmaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
