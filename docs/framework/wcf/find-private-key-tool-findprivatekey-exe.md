---
description: 'Hakkında daha fazla bilgi edinin: özel anahtar aracını bul (FindPrivateKey.exe)'
title: Find Private Key Aracı (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 1d87d19e17c1de89c13db6d7ca092eedf630e6ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793292"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="d3bcf-103">Find Private Key Aracı (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="d3bcf-103">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="d3bcf-104">Bu komut satırı aracı, bir sertifika deposundan özel anahtar almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-104">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="d3bcf-105">Örneğin, *FindPrivateKey.exe* , sertifika deposundaki belirli bir X. 509.440 sertifikasıyla ilişkili özel anahtar dosyasının konumunu ve adını bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-105">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3bcf-106">FindPrivateKey aracı bir WCF örneği olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-106">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="d3bcf-107">Örneği nerede bulabileceğiniz ve nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="d3bcf-107">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="d3bcf-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3bcf-108">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="d3bcf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3bcf-109">Remarks</span></span>

<span data-ttu-id="d3bcf-110">Aşağıdaki tablolar, özel anahtar Bul Aracı (FindPrivateKey.exe) ile kullanılabilen bağımsız değişkenleri ve seçenekleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-110">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="d3bcf-111">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="d3bcf-111">Argument</span></span>|<span data-ttu-id="d3bcf-112">Description</span><span class="sxs-lookup"><span data-stu-id="d3bcf-112">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="d3bcf-113">Sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-113">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="d3bcf-114">Sertifika deposunun konumu.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-114">The location of the certificate store.</span></span>|

|<span data-ttu-id="d3bcf-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d3bcf-115">Option</span></span>|<span data-ttu-id="d3bcf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3bcf-116">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="d3bcf-117">`/n <`*SubjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="d3bcf-117">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="d3bcf-118">Sertifikanın konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-118">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="d3bcf-119">`/t <`*parmak izi*`>`</span><span class="sxs-lookup"><span data-stu-id="d3bcf-119">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="d3bcf-120">Sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-120">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="d3bcf-121">Sertifikanın parmak izini almak için Certmgr.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-121">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="d3bcf-122">Yalnızca dosya adını verir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-122">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="d3bcf-123">Yalnızca dizinin çıktısını verir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-123">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="d3bcf-124">Mutlak dosya adını verir.</span><span class="sxs-lookup"><span data-stu-id="d3bcf-124">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="d3bcf-125">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d3bcf-125">Examples</span></span>

<span data-ttu-id="d3bcf-126">Aşağıdaki komut John tikan için özel anahtarı alır:</span><span class="sxs-lookup"><span data-stu-id="d3bcf-126">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="d3bcf-127">Aşağıdaki komut yerel makinenin özel anahtarını alır:</span><span class="sxs-lookup"><span data-stu-id="d3bcf-127">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
