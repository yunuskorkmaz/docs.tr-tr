---
title: Find Private Key Aracı (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 00ad27d28ee3a589d5ee8702bd036b05d8ceb4b3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637568"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Find Private Key Aracı (FindPrivateKey.exe)

Bu komut satırı aracı, sertifika deposundan bir özel anahtarı almak için kullanılabilir. Örneğin, *FindPrivateKey.exe* sertifika deposundaki belirli bir X.509 sertifikasıyla ilişkili özel anahtar dosyasının adını ve konumunu bulmak için kullanılabilir.

> [!IMPORTANT]
> FindPrivateKey aracı WCF örnek olarak sevk edilir. Örnek nerede bulacağını ve bu yapı hakkında daha fazla bilgi için bkz. [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Sözdizimi

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablolarda, bağımsız değişkenler ve özel anahtar Bul Aracı (FindPrivateKey.exe) kullanılabilir seçenekler açıklanmaktadır.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`storeName`|Sertifika deposu adı.|
|`storeLocation`|Sertifika depolama konumu.|

|Seçenek|Açıklama|
|------------|-----------------|
|`/n <` *SubjectName* `>`|Sertifikanın konu adını belirtir.|
|`/t <` *parmak izi* `>`|Sertifikanın parmak izini belirtir. Certmgr.exe sertifikanın parmak izini almak için kullanın.|
|`/f`|Yalnızca dosya adını çıkarır.|
|`/d`|Yalnızca dizine çıkarır.|
|`/a`|Mutlak dosya adı çıkarır.|

## <a name="examples"></a>Örnekler

Aşağıdaki komut, özel anahtarı için John Doe alır:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Aşağıdaki komut, yerel makine özel anahtarını alır:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
