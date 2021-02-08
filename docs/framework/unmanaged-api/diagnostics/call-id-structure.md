---
description: 'Daha fazla bilgi edinin: CALL_ID yapısı'
title: CALL_ID Yapısı
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 4ef6023e382e8c5fead48494f428648a37f3bef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800493"
---
# <a name="call_id-structure"></a>CALL_ID Yapısı

Çağrılmakta olan bir işlev hakkında bilgi bir hata ayıklayıcıyla ilgili bilgiler sağlar. Daha fazla bilgi için bkz. [INotifySink2](inotifysink2-interface.md) arabirimi.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`szMachine`|Çağrıyı yapan makineyi tanımlar.|  
|`dwPid`|Makine işlemcisini tanımlar.|  
|`pUserThread`|Çağrıyı yürüten iş parçacığını tanımlar.|  
|`addrStackPointer`|Çağrı yığınının adresini belirtir.|  
|`szEntryPoint`|Çağrının adresini belirtir.|  
|`szDestinationMachine`|Çağrıyı yürütecek makineyi tanımlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](inotifysink2-interface.md)
- [Tanılama Sembol Deposu Yapıları](diagnostics-symbol-store-structures.md)
