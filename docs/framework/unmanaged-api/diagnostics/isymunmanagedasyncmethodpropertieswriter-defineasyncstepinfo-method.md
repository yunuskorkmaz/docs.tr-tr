---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f8c77e44183fd92704aa91ca1cfd7e3fa68aa27f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719625"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi

Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.  
  
 Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar. Her bir `breakpointMethod` / `breakpointOffset` çiftin, zaman uyumsuz işlemin sürdürülecek, farklı bir yöntemde olabilecek bir durum olduğunu söyler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a>Dönüş Değeri  

 `HRESULT` döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](isymunmanagedasyncmethodpropertieswriter-interface.md)
