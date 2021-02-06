---
description: 'Daha fazla bilgi edinin: CreateALink Işlevi'
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
ms.openlocfilehash: cf34ae8d38a8339f539c770df8f5dd14e4a3e4b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638372"
---
# <a name="createalink-function"></a>CreateALink İşlevi

Derleme bağlayıcının bir örneğini oluşturur ve belirtilen arabirime bir işaretçi ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`riid`|Bütünleştirilmiş kod bağlayıcı arabirimlerinden birinin fiziksel adı.|  
|`ppInterface`|Başarılı tamamlamadaki konum, arabirime yönelik bir işaretçi içerir `riid` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../tools/al-exe-assembly-linker.md)
