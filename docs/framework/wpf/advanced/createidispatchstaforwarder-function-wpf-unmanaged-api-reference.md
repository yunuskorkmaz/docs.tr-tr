---
title: "CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder işlevi (WPF yönetilmeyen API Başvurusu)
Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.  
  
 Windows Presentation Foundation (WPF) altyapısı tarafından iş parçacığı ve windows yönetimi için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a>Parametreler  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 pDispatchDelegate  
 Bir işaretçi bir `IDispatch` arabirimi.  
  
 ppForwarder  
 Adresine bir işaretçi bir `IDispatch` arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [.NET Framework sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 .NET Framework 3.0 ve 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 ve üzeri: PresentationHost_v0400.dll  
  
 **.NET framework sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF yönetilmeyen API Başvurusu](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
