---
title: Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49a5ad951c47100199c93d03efb07ffc6fda5080
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851424"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="4e53e-102">Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)</span><span class="sxs-lookup"><span data-stu-id="4e53e-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="4e53e-103">Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e53e-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="4e53e-104">Cert2spc.exe, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="4e53e-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="4e53e-105">VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e53e-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="4e53e-106">X. 509.952 sertifikaları oluşturma hakkında daha fazla bilgi için bkz. [MakeCert. exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="4e53e-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="4e53e-107">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4e53e-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4e53e-108">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e53e-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4e53e-109">Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4e53e-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4e53e-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="4e53e-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e53e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e53e-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e53e-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e53e-112">Parameters</span></span>  
  
|<span data-ttu-id="4e53e-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="4e53e-113">Argument</span></span>|<span data-ttu-id="4e53e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e53e-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="4e53e-115">SPC dosyasına eklenecek bir X.509 sertifikasının adı.</span><span class="sxs-lookup"><span data-stu-id="4e53e-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="4e53e-116">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e53e-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="4e53e-117">SPC dosyasına eklenecek bir sertifika iptal listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="4e53e-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="4e53e-118">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e53e-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="4e53e-119">X.509 sertifikaları içeren PKCS #7 nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="4e53e-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="4e53e-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="4e53e-120">Option</span></span>|<span data-ttu-id="4e53e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e53e-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4e53e-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="4e53e-122">**/?**</span></span>|<span data-ttu-id="4e53e-123">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4e53e-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="4e53e-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4e53e-124">Examples</span></span>  
 <span data-ttu-id="4e53e-125">Aşağıdaki komut, ' dan `myCertificate.cer` bir SPC oluşturur ve bunu içine `mySPCFile.spc`koyar.</span><span class="sxs-lookup"><span data-stu-id="4e53e-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="4e53e-126">Aşağıdaki komut, ve `oneCertificate.cer` `twoCertificate.cer`' dan bir SPC oluşturur ve içine `mySPCFile.spc`koyar.</span><span class="sxs-lookup"><span data-stu-id="4e53e-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e53e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e53e-127">See also</span></span>

- [<span data-ttu-id="4e53e-128">Araçlar</span><span class="sxs-lookup"><span data-stu-id="4e53e-128">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="4e53e-129">MakeCert. exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="4e53e-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="4e53e-130">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="4e53e-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
