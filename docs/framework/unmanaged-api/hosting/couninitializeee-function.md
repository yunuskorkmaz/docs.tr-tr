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
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687853"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE İşlevi

`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlev sağlamaz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor. Yürütme altyapısını kapatmak için, [CorExitProcess](corexitprocess-function.md)çağrısını çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CoInitializeEE İşlevi](coinitializeee-function.md)
- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
