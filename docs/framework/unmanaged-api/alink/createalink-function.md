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
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446546"
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
|`ppInterface`|Başarılı tamamlamada yer alan konum `riid` arabirimine yönelik bir işaretçi içerir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Kitaplık**: ALink. dll  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../tools/al-exe-assembly-linker.md)
