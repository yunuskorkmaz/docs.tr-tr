---
title: Find Private Key Aracı (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498520"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Find Private Key Aracı (FindPrivateKey.exe)

Bu komut satırı aracı, sertifika deposundan bir özel anahtar almak için kullanılabilir. Örneğin, *FindPrivateKey.exe* belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak için kullanılır.

> [!IMPORTANT]
> FindPrivateKey aracı bir WCF örnek olarak geliyordu. Örnek nerede bulacağını ve bu derleme hakkında daha fazla bilgi için bkz: [FindPrivateKey](./samples/findprivatekey.md).

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
|`/n <` *SubjectName* `>`|Sertifikasının konu adını belirtir.|
|`/t <` *parmak izi* `>`|Sertifikanın parmak izi belirtir. Certmgr.exe sertifikanın parmak izi almak için kullanın.|
|`/f`|Yalnızca dosya adını çıkarır.|
|`/d`|Dizin yalnızca çıkarır.|
|`/a`|Mutlak dosya adı çıkarır.|

## <a name="examples"></a>Örnekler

Aşağıdaki komut John Doe için özel anahtarı alır:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Aşağıdaki komut, özel anahtarı yerel makinede alır:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```