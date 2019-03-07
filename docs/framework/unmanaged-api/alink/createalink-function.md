---
title: CreateALink İşlevi
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498019"
---
# <a name="createalink-function"></a>CreateALink İşlevi
Assembly Linker örneği oluşturur ve belirtilen arabirim için bir işaretçi ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`riid`|Assembly Linker arabirimlerinden birini fiziksel adı.|  
|`ppInterface`|Başarıyla tamamlandığında bir işaretçi içeren konuma `riid` arabirimi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
