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
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400672"
---
# <a name="createalink-function"></a>CreateALink İşlevi
Derleme Bağlayıcı örneği oluşturur ve belirtilen arabirime bir işaretçi ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`riid`|Derleme Bağlayıcı arabirimlerinden biri, fiziksel adı.|  
|`ppInterface`|Başarıyla tamamlandığında bir işaretçi içeren konuma `riid` arabirimi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
