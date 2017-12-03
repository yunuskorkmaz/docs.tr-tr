---
title: "Find Private Key Aracı (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Find Private Key Aracı (FindPrivateKey.exe)
Bu komut satırı aracı, sertifika deposundan bir özel anahtar almak için kullanılabilir. Örneğin, FindPrivateKey.exe belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak için kullanılabilir.  
  
> [!IMPORTANT]
>  FindPrivateKey aracı bir WCF örnek olarak geliyordu. Örnek nerede bulacağını ve bu derleme hakkında daha fazla bilgi için bkz:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablolarda, değişkenler ve özel anahtar Bul Aracı (FindPrivateKey.exe) ile kullanılabilir seçenekler açıklanmaktadır.  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`storeName`|Sertifika deposu adı.|  
|`storeLocation`|Sertifika deposu konumu.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|Sertifikasının konu adını belirtir.|  
|`/t <`*parmak izi*`>`|Sertifikanın parmak izi belirtir. Certmgr.exe sertifikanın parmak izi almak için kullanın.|  
|`/f`|Yalnızca dosya adını çıkarır.|  
|`/d`|Dizin yalnızca çıkarır.|  
|`/a`|Mutlak dosya adı çıkarır.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, John Doe için özel anahtarı alır.  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 Aşağıdaki komut, özel anahtarı yerel makinede alır.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
