---
title: IMetaDataImport::FindField Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503673"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField Yöntemi
Belirtilen <xref:System.Type> ve belirtilen ad ve meta veri imzasına sahip olan alan Için FieldDef belirtecine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `td`  
 'ndaki Aranacak alanı kapsayan sınıf veya arabirim için TypeDef belirteci. Bu değer ise `mdTokenNil` , arama genel bir değişken için yapılır.  
  
 `szName`  
 'ndaki Aranacak alanın adı.  
  
 `pvSigBlob`  
 'ndaki Alanın ikili meta veri imzasına yönelik bir işaretçi.  
  
 `cbSigBlob`  
 'ndaki Bayt cinsinden boyut `pvSigBlob` .  
  
 `pmb`  
 dışı Eşleşen FieldDef belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Alanı kapsayan sınıfını veya arabirimini ( `td` ), adını ( `szName` ) ve isteğe bağlı olarak imzasını () kullanarak belirtirsiniz `pvSigBlob` .  
  
 `FindField`İmzaların belirli bir kapsama bağlandığı için, geçirilen imza geçerli kapsamda oluşturulmuş olmalıdır. İmza, kapsayan sınıf veya değer türünü tanımlayan bir belirteç ekleyebilir. (Belirteç yerel TypeDef tablosunun bir dizinidir). Geçerli kapsamın bağlamı dışında bir çalışma zamanı imzası derlenemez ve bu imzayı giriş olarak kullanabilirsiniz `FindField` .  
  
 `FindField`yalnızca sınıfta veya arabirimde doğrudan tanımlanmış alanları bulur; devralınan alanları bulamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
