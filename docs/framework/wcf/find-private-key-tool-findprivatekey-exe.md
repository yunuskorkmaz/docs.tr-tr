---
title: Find Private Key Aracı (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990348"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Find Private Key Aracı (FindPrivateKey.exe)

Bu komut satırı aracı, bir sertifika deposundan özel anahtar almak için kullanılabilir. Örneğin, *FindPrivateKey. exe* , sertifika deposundaki belirli bir X. 509.440 sertifikasıyla ilişkili özel anahtar dosyasının konumunu ve adını bulmak için kullanılabilir.

> [!IMPORTANT]
> FindPrivateKey aracı bir WCF örneği olarak gönderilir. Örneği nerede bulabileceğiniz ve nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Sözdizimi

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablolar, özel anahtar Bul Aracı (FindPrivateKey. exe) ile kullanılabilen bağımsız değişkenleri ve seçenekleri anlatmaktadır.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`storeName`|Sertifika deposunun adı.|
|`storeLocation`|Sertifika deposunun konumu.|

|Seçenek|Açıklama|
|------------|-----------------|
|`/n <`*SubjectName*`>`|Sertifikanın konu adını belirtir.|
|`/t <`*parmak izi*`>`|Sertifikanın parmak izini belirtir. Sertifikanın parmak izini almak için certmgr. exe ' yi kullanın.|
|`/f`|Yalnızca dosya adını verir.|
|`/d`|Yalnızca dizinin çıktısını verir.|
|`/a`|Mutlak dosya adını verir.|

## <a name="examples"></a>Örnekler

Aşağıdaki komut John tikan için özel anahtarı alır:

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Aşağıdaki komut yerel makinenin özel anahtarını alır:

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
