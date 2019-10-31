---
title: CoUninitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136857"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE İşlevi
`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlev sağlamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor. Yürütme altyapısını kapatmak için, [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)çağrısını çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CoInitializeEE İşlevi](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
