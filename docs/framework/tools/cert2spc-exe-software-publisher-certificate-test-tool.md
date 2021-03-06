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
ms.openlocfilehash: 96b4c05f6c9af6fc78aa55b248a88de84e2d4ac8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258292"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="de98f-104">Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)</span><span class="sxs-lookup"><span data-stu-id="de98f-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>

<span data-ttu-id="de98f-105">Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de98f-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="de98f-106">Cert2spc.exe, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="de98f-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="de98f-107">VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de98f-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="de98f-108">X. 509.440 sertifikaları oluşturma hakkında daha fazla bilgi için bkz. [Makecert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="de98f-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="de98f-109">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="de98f-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="de98f-110">Aracı çalıştırmak için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="de98f-110">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="de98f-111">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="de98f-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de98f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de98f-112">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="de98f-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de98f-113">Parameters</span></span>  
  
|<span data-ttu-id="de98f-114">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="de98f-114">Argument</span></span>|<span data-ttu-id="de98f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de98f-115">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="de98f-116">SPC dosyasına eklenecek bir X.509 sertifikasının adı.</span><span class="sxs-lookup"><span data-stu-id="de98f-116">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="de98f-117">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de98f-117">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="de98f-118">SPC dosyasına eklenecek bir sertifika iptal listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="de98f-118">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="de98f-119">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de98f-119">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="de98f-120">X.509 sertifikaları içeren PKCS #7 nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="de98f-120">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="de98f-121">Seçenek</span><span class="sxs-lookup"><span data-stu-id="de98f-121">Option</span></span>|<span data-ttu-id="de98f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de98f-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="de98f-123">**/?**</span><span class="sxs-lookup"><span data-stu-id="de98f-123">**/?**</span></span>|<span data-ttu-id="de98f-124">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de98f-124">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="de98f-125">Örnekler</span><span class="sxs-lookup"><span data-stu-id="de98f-125">Examples</span></span>  

 <span data-ttu-id="de98f-126">Aşağıdaki komut, ' dan bir SPC oluşturur `myCertificate.cer` ve bunu içine koyar `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="de98f-126">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="de98f-127">Aşağıdaki komut, ve ' dan bir SPC oluşturur `oneCertificate.cer` `twoCertificate.cer` ve içine koyar `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="de98f-127">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="de98f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de98f-128">See also</span></span>

- [<span data-ttu-id="de98f-129">Araçlar</span><span class="sxs-lookup"><span data-stu-id="de98f-129">Tools</span></span>](index.md)
- [<span data-ttu-id="de98f-130">Makecert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="de98f-130">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="de98f-131">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="de98f-131">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
