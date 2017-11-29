---
title: "Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c720da81c63b612201ede5f648f6861470b25bee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="b9d22-102">Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)</span><span class="sxs-lookup"><span data-stu-id="b9d22-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="b9d22-103">Yazılım Yayımcı Sertifikası Test aracı, bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcısı Sertifikası (SPC) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9d22-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="b9d22-104">Cert2spc.exe, yalnızca test amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="b9d22-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="b9d22-105">VeriSign ya da Thawte gibi bir Sertifika Yetkilisi'nden geçerli bir SPC edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9d22-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="b9d22-106">X.509 sertifikaları oluşturma hakkında daha fazla bilgi için bkz: [Makecert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span><span class="sxs-lookup"><span data-stu-id="b9d22-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).</span></span>  
  
 <span data-ttu-id="b9d22-107">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b9d22-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b9d22-108">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b9d22-108">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b9d22-109">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b9d22-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b9d22-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="b9d22-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d22-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9d22-111">Syntax</span></span>  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9d22-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9d22-112">Parameters</span></span>  
  
|<span data-ttu-id="b9d22-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="b9d22-113">Argument</span></span>|<span data-ttu-id="b9d22-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9d22-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="b9d22-115">SPC dosyasına eklenecek bir X.509 sertifikasının adı.</span><span class="sxs-lookup"><span data-stu-id="b9d22-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="b9d22-116">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9d22-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="b9d22-117">SPC dosyasına eklenecek bir sertifika iptal listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="b9d22-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="b9d22-118">Boşluklarla ayırarak birden fazla ad belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9d22-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="b9d22-119">X.509 sertifikaları içeren PKCS #7 nesnesinin adı.</span><span class="sxs-lookup"><span data-stu-id="b9d22-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="b9d22-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="b9d22-120">Option</span></span>|<span data-ttu-id="b9d22-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9d22-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b9d22-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="b9d22-122">**/?**</span></span>|<span data-ttu-id="b9d22-123">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b9d22-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="b9d22-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b9d22-124">Examples</span></span>  
 <span data-ttu-id="b9d22-125">Aşağıdaki komut bir SPC gelen oluşturur `myCertificate.cer` ve yerleştirir `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="b9d22-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="b9d22-126">Aşağıdaki komut bir SPC gelen oluşturur `oneCertificate.cer` ve `twoCertificate.cer`ve yerleştirir `mySPCFile.spc`.</span><span class="sxs-lookup"><span data-stu-id="b9d22-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9d22-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9d22-127">See Also</span></span>  
 [<span data-ttu-id="b9d22-128">Araçları</span><span class="sxs-lookup"><span data-stu-id="b9d22-128">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="b9d22-129">MakeCert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="b9d22-129">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="b9d22-130">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="b9d22-130">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
