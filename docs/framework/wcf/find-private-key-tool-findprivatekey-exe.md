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
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="4966f-102">Find Private Key Aracı (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="4966f-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="4966f-103">Bu komut satırı aracı, sertifika deposundan bir özel anahtarı almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4966f-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="4966f-104">Örneğin, *FindPrivateKey.exe* sertifika deposundaki belirli bir X.509 sertifikasıyla ilişkili özel anahtar dosyasının adını ve konumunu bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4966f-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4966f-105">FindPrivateKey aracı WCF örnek olarak sevk edilir.</span><span class="sxs-lookup"><span data-stu-id="4966f-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="4966f-106">Örnek nerede bulacağını ve bu yapı hakkında daha fazla bilgi için bkz. [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="4966f-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="4966f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4966f-107">Syntax</span></span>

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="4966f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4966f-108">Remarks</span></span>

<span data-ttu-id="4966f-109">Aşağıdaki tablolarda, bağımsız değişkenler ve özel anahtar Bul Aracı (FindPrivateKey.exe) kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4966f-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="4966f-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="4966f-110">Argument</span></span>|<span data-ttu-id="4966f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4966f-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="4966f-112">Sertifika deposu adı.</span><span class="sxs-lookup"><span data-stu-id="4966f-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="4966f-113">Sertifika depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="4966f-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="4966f-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="4966f-114">Option</span></span>|<span data-ttu-id="4966f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4966f-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="4966f-116">`/n <` *SubjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="4966f-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="4966f-117">Sertifikanın konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4966f-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="4966f-118">`/t <` *parmak izi* `>`</span><span class="sxs-lookup"><span data-stu-id="4966f-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="4966f-119">Sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4966f-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="4966f-120">Certmgr.exe sertifikanın parmak izini almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4966f-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="4966f-121">Yalnızca dosya adını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4966f-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="4966f-122">Yalnızca dizine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4966f-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="4966f-123">Mutlak dosya adı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4966f-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="4966f-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4966f-124">Examples</span></span>

<span data-ttu-id="4966f-125">Aşağıdaki komut, özel anahtarı için John Doe alır:</span><span class="sxs-lookup"><span data-stu-id="4966f-125">The following command retrieves the private key for John Doe:</span></span>

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="4966f-126">Aşağıdaki komut, yerel makine özel anahtarını alır:</span><span class="sxs-lookup"><span data-stu-id="4966f-126">The following command retrieves the private key for the local machine:</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
