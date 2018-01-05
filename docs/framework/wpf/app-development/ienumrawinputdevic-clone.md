---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db218ec824dfe163946b0c1bd412efd0f78f4ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Aynı liste üzerinde yinelemek için geçerli Numaralandırıcı ile aynı duruma sahip başka bir ham giriş aygıt numaralandırıcısı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppenum`  
  
 [out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) arabirim işaretçisi. Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımlanmamıştır.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: Bu yöntem E_INVALIDARG, E_OUTOFMEMORY ve E_UNEXPECTED standart dönüş değerlerini destekler.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem daha sonraki bir zamanda bu noktaya kadar dönebilmek için numaralandırma sırayla bir noktası kaydetmek mümkün kılar. Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak serbest bırakmanız gerekir.
