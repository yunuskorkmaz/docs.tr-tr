---
title: Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
description: Yazılım yayımcısı sertifika test aracı Cert2spc.exe kullanın. Bu araç bir veya daha fazla X. 509.440 sertifikasından bir yazılım yayımcısı sertifikası (SPC) oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 2eb6339aa6f5d23a5b87986410cbeaac2dac2bec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167319"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="57164-104">Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)</span><span class="sxs-lookup"><span data-stu-id="57164-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="57164-105">Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57164-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="57164-106">Cert2spc.exe, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="57164-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="57164-107">VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57164-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="57164-108">X. 509.440 sertifikaları oluşturma hakkında daha fazla bilgi için bkz. [Makecert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="57164-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="57164-109">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="57164-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="57164-110">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="57164-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="57164-111">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="57164-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="57164-112">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="57164-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57164-113">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="57164-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="57164-114">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57164-114">Parameters</span></span>  
  
|<span data-ttu-id="57164-115">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="57164-115">Argument</span></span>|<span data-ttu-id="57164-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57164-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="57164-117">SPC dosyasına eklenecek bir X.509 sertifikasının adı.</span><span class="sxs-lookup"><span data-stu-id="57164-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="57164-118">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57164-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="57164-119">SPC dosyasına eklenecek bir sertifika iptal listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="57164-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="57164-120">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57164-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="57164-121">X.509 sertifikaları içeren PKCS #7 nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="57164-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="57164-122">Seçenek</span><span class="sxs-lookup"><span data-stu-id="57164-122">Option</span></span>|<span data-ttu-id="57164-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57164-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="57164-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="57164-124">**/?**</span></span>|<span data-ttu-id="57164-125">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="57164-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="57164-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="57164-126">Examples</span></span>  
 <span data-ttu-id="57164-127">Aşağıdaki komut, ' dan bir SPC oluşturur `myCertificate.cer` ve bunu içine koyar `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="57164-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="57164-128">Aşağıdaki komut, ve ' dan bir SPC oluşturur `oneCertificate.cer` `twoCertificate.cer` ve içine koyar `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="57164-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="57164-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57164-129">See also</span></span>

- [<span data-ttu-id="57164-130">Araçlar</span><span class="sxs-lookup"><span data-stu-id="57164-130">Tools</span></span>](index.md)
- [<span data-ttu-id="57164-131">Makecert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="57164-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="57164-132">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="57164-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
