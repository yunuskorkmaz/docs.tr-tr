---
description: 'Daha fazla bilgi edinin: EmitManifest yöntemi'
title: EmitManifest Yöntemi
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: 770631864c030c067feb0b02d2f00c36076aa44c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638281"
---
# <a name="emitmanifest-method"></a>EmitManifest Yöntemi

Son bildirimi yayar. Diğer tüm dosyaları içeri aktardıktan sonra ve tüm seçenekleri ayarlayarak bu yöntemi çağırın. İlişkisiz modüller için bu yöntemi çağırmayın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `pdwReserveSize`  
 [Strongnametabeturesize işlevinden](../strong-naming/strongnamesignaturesize-function.md)alınan derleme dosyasında ayrılacak boyutu alır.  
  
 `ptkManifest`  
 İsteğe bağlı olarak, derleme bildirimi belirtecini alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
