---
title: IMetaDataImport2::GetVersionString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a01b4203145f6ffee4e3a11a3526f0b83e3dc741
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042529"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString Metodu
Derlemesi oluşturmak için kullanılan çalışma zamanı sürüm numarasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwzBuf`  
 [out] Sürümünü belirten bir dize depolamak için bir dizi.  
  
 `ccBufSize`  
 [in] Geniş karakter cinsinden boyutu, `pwzBuf` dizisi.  
  
 `pccBufSize`  
 [out] Null sonlandırıcıyı da dahil olmak üzere geniş karakter sayısına göre döndürülen `pwzBuf` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetVersionString` Yöntemi geçerli meta veri kapsamı için yerleşik sürümünü alır. Kapsamı hiç kaydedilmemişse, yerleşik bir sürüm olmaz ve boş bir dize döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
