---
description: 'Daha fazla bilgi edinin: GetWin32ResBlob yöntemi'
title: GetWin32ResBlob Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
ms.openlocfilehash: e1140b14bfba56dfac03c443a537d6d2188575b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718271"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob Metodu

Win32 kaynak blobu alır. Derleme seçeneklerini ayarladıktan sonra bu yöntemi çağırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  

 `AssemblyID`  
 Derlemenin KIMLIĞI.  
  
 `FileToken`  
 Win32 sürüm kaynağı oluşturulurken kullanılacak dosya adını almak için kullanılan dosya belirteci  
  
 `fDll`  
 Dosya DLL ise TRUE, bir EXE için false.  
  
 `pszIconFile`  
 Kaynak blobuna eklenecek isteğe bağlı simge.  
  
 `ppResBlob`  
 Kaynak blobu alır.  
  
 `pcbResBlob`  
 Blobun boyutunu alır.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 ALink. h gerektirir  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink Arabirimi](ialink-interface.md)
- [IALink2 Arabirimi](ialink2-interface.md)
- [ALink API](index.md)
