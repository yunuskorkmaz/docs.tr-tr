---
title: IMetaDataImport::GetParamForMethodIndex Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: 21a83e404405ca9cfe301b76cb1e1591d69e747c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491127"
---
# <a name="imetadataimportgetparamformethodindex-method"></a>IMetaDataImport::GetParamForMethodIndex Yöntemi
Belirtilen MethodDef belirteci tarafından temsil edilen metodun belirtilen bir parametresini temsil eden belirteci alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `md`  
 'ndaki İçin parametre belirtecini döndürecek yöntemi temsil eden bir belirteç.  
  
 `ulParamSeq`  
 'ndaki İstenen parametrenin gerçekleştiği parametre listesindeki sıra konumu. Parametreler, bir öğesinden başlayarak, yöntemin sıfır konumundaki dönüş değeri ile numaralandırılır.  
  
 `ppd`  
 dışı İstenen parametreyi temsil eden bir ParamDef belirtecinin işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
