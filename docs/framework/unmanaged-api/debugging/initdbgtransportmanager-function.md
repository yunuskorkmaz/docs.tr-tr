---
title: InitDbgTransportManager İşlevi
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423669"
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager İşlevi
İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başarılı.  
  
 E_OUTOFMEMORY  
 İşlevi için bir aktarım Yöneticisi bellek ayıramadı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer hataları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kitaplığı:** mscordbi_macx86.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
