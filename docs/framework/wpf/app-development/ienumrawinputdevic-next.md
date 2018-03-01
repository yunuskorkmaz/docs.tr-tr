---
title: IEnumRAWINPUTDEVIC:Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af6cb5bfe07923e13f1b76c785d830a9af15eaf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Sonraki numaralandırır `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) yapıları Numaralandırıcının listesi içinde `rgelt` numaralandırılmış öğelerin gerçek sayısını birlikte `pceltFetched`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
  
 [in] Sayısı [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) döndürülen yapıları `rgelt`.  
  
 `rgelt`  
  
 [out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).  
  
 `pceltFetched`  
  
 [out] İşaretçi gerçekte içinde sağlanan öğe sayısı için `rgelt`. Arayan geçirebilir `NULL` varsa `rgelt` biridir.  
  
## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri  
 HRESULT: sağlanan öğe sayısı ise S_OK `celt`; Aksi durumda S_FALSE.
