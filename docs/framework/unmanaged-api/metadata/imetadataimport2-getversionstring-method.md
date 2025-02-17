---
description: ': IMetaDataImport2:: GetVersionString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688565"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString Metodu

Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzBuf`  
 dışı Sürümü belirten dizeyi depolayan bir dizi.  
  
 `ccBufSize`  
 'ndaki Dizinin geniş karakterdeki boyutu `pwzBuf` .  
  
 `pccBufSize`  
 dışı Dizide döndürülen bir null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pwzBuf` .  
  
## <a name="remarks"></a>Açıklamalar  

 `GetVersionString`Yöntemi, geçerli meta veri kapsamının yerleşik sürümünü alır. Kapsam hiç kaydedilmediğinde, yerleşik bir sürüme sahip olmaz ve boş bir dize döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
