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
ms.openlocfilehash: b494b8b776f4cb0eb534233c5a03ab2d34a698ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115628"
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
