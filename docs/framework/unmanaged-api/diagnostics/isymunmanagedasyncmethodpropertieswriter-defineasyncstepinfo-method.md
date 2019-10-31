---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129191"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Yöntemi
Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.  
  
 Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar. Her bir `breakpointMethod`/`breakpointOffset` çifti, zaman uyumsuz işlemin sürdürülecek farklı bir yöntemde olabilecek olduğunu bize söyler.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 `HRESULT`döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
