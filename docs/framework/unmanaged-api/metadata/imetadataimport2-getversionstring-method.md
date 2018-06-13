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
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448732"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString Metodu
Derleme oluşturma için kullanılan çalışma zamanı sürüm numarasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwzBuf`  
 [out] Sürüm belirten bir dize depolamak için bir dizi.  
  
 `ccBufSize`  
 [in] Geniş karakterler boyutu, `pwzBuf` dizi.  
  
 `pccBufSize`  
 [out] Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını döndürülen `pwzBuf` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetVersionString` Yöntemi geçerli meta veri kapsamı yerleşik için sürümünü alır. Kapsam hiçbir zaman kaydedilmişse, bir yerleşik için sürümüne sahip değil ve boş bir dize döndürdü.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
