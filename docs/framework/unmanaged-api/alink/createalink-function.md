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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787624"
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
|`ppInterface`|Başarılı tamamlamadaki konum, `riid` arabirime yönelik bir işaretçi içerir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Kitaplık**: ALink. dll  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../tools/al-exe-assembly-linker.md)
