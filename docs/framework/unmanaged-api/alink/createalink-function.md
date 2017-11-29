---
title: "CreateALink İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a102e9601f751ee8c7e325293e83467b1314ff41
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Al.exe (derleme bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
