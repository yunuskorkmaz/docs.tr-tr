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
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="453a3-102">Find Private Key Aracı (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="453a3-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="453a3-103">Bu komut satırı aracı, bir sertifika deposundan özel anahtar almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="453a3-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="453a3-104">Örneğin, *FindPrivateKey. exe* , sertifika deposundaki belirli bir X. 509.440 sertifikasıyla ilişkili özel anahtar dosyasının konumunu ve adını bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="453a3-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="453a3-105">FindPrivateKey aracı bir WCF örneği olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="453a3-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="453a3-106">Örneği nerede bulabileceğiniz ve nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="453a3-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="453a3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="453a3-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="453a3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="453a3-108">Remarks</span></span>

<span data-ttu-id="453a3-109">Aşağıdaki tablolar, özel anahtar Bul Aracı (FindPrivateKey. exe) ile kullanılabilen bağımsız değişkenleri ve seçenekleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="453a3-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="453a3-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="453a3-110">Argument</span></span>|<span data-ttu-id="453a3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="453a3-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="453a3-112">Sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="453a3-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="453a3-113">Sertifika deposunun konumu.</span><span class="sxs-lookup"><span data-stu-id="453a3-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="453a3-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="453a3-114">Option</span></span>|<span data-ttu-id="453a3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="453a3-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="453a3-116">`/n <`*SubjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="453a3-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="453a3-117">Sertifikanın konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="453a3-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="453a3-118">`/t <`*parmak izi*`>`</span><span class="sxs-lookup"><span data-stu-id="453a3-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="453a3-119">Sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="453a3-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="453a3-120">Sertifikanın parmak izini almak için certmgr. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="453a3-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="453a3-121">Yalnızca dosya adını verir.</span><span class="sxs-lookup"><span data-stu-id="453a3-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="453a3-122">Yalnızca dizinin çıktısını verir.</span><span class="sxs-lookup"><span data-stu-id="453a3-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="453a3-123">Mutlak dosya adını verir.</span><span class="sxs-lookup"><span data-stu-id="453a3-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="453a3-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="453a3-124">Examples</span></span>

<span data-ttu-id="453a3-125">Aşağıdaki komut John tikan için özel anahtarı alır:</span><span class="sxs-lookup"><span data-stu-id="453a3-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="453a3-126">Aşağıdaki komut yerel makinenin özel anahtarını alır:</span><span class="sxs-lookup"><span data-stu-id="453a3-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
