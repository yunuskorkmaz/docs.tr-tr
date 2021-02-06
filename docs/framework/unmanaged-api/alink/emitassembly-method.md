---
description: 'Daha fazla bilgi edinin: EmitAssembly yöntemi'
title: EmitAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: aada17d8df6435c5edfe6beb5db5ee13f887f253
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638346"
---
# <a name="emitassembly-method"></a>EmitAssembly Yöntemi

Derlemeyi oluşturur. Derleme dosyası hariç diğer tüm dosyalar kapatıldıktan sonra bu yöntemi çağırın. İlişkisiz modüller üretilirken bu yöntemi çağırmayın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
