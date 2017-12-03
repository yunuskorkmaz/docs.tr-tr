---
title: "Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e03a38e2a93dd866bc3da65527d5410b09009e00
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="56624-102">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="56624-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="56624-103">Bir X.509 sertifikası erişilebilir olmasını sağlamak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], uygulama kodu sertifika deposu adını ve konumunu belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="56624-103">To make an X.509 certificate accessible to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], application code must specify the certificate store name and location.</span></span> <span data-ttu-id="56624-104">Bazı durumlarda, işlem kimliği, X.509 sertifikayla ilişkili özel anahtarı içeren dosyayı için erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56624-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="56624-105">Bir sertifika deposunda bir X.509 sertifikası ile ilişkili özel anahtarı edinme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bunu yapmak için izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56624-105">To obtain the private key associated with an X.509 certificate in a certificate store, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must have permission to do so.</span></span> <span data-ttu-id="56624-106">Varsayılan olarak, yalnızca sahibi ve sistem hesabı, bir sertifikanın özel anahtarı erişebilir.</span><span class="sxs-lookup"><span data-stu-id="56624-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="56624-107">X.509 sertifikalarını WCF için erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="56624-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="56624-108">Hesap vermek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikayla ilişkili özel anahtarı içeren dosya için okuma erişimi çalıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="56624-108">Give the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="56624-109">Belirlemek olup olmadığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 Sertifika özel anahtarına okuma erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56624-109">Determine whether [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="56624-110">Bir özel anahtar bir X.509 sertifikası kullanırken kullanılabilir olmalıdır yoksa aşağıdaki tabloda ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56624-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="56624-111">X.509 sertifika kullan</span><span class="sxs-lookup"><span data-stu-id="56624-111">X.509 certificate use</span></span>|<span data-ttu-id="56624-112">Özel anahtar</span><span class="sxs-lookup"><span data-stu-id="56624-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="56624-113">Giden SOAP ileti dijital olarak imzalamak.</span><span class="sxs-lookup"><span data-stu-id="56624-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="56624-114">Evet</span><span class="sxs-lookup"><span data-stu-id="56624-114">Yes</span></span>|  
        |<span data-ttu-id="56624-115">Gelen bir SOAP iletisi imzası doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="56624-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="56624-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="56624-116">No</span></span>|  
        |<span data-ttu-id="56624-117">Giden SOAP ileti şifreleme.</span><span class="sxs-lookup"><span data-stu-id="56624-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="56624-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="56624-118">No</span></span>|  
        |<span data-ttu-id="56624-119">Gelen bir SOAP iletisi çözme.</span><span class="sxs-lookup"><span data-stu-id="56624-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="56624-120">Evet</span><span class="sxs-lookup"><span data-stu-id="56624-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="56624-121">Sertifikanın depolandığı adı ve sertifika deposu konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="56624-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="56624-122">Sertifikanın depolandığı sertifika deposu uygulama kodu veya yapılandırmasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="56624-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="56624-123">Örneğin, aşağıdaki örnek sertifika bulunan belirtir `CurrentUser` adlı sertifika deposuna `My`.</span><span class="sxs-lookup"><span data-stu-id="56624-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="56624-124">Kullanarak, sertifikanın özel anahtarı bilgisayarda bulunduğu belirlemek [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="56624-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="56624-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika depolama alanı adı, sertifika deposu konumu ve sertifika benzersiz olarak tanımlayan bir şey gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56624-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="56624-126">Aracı sertifikanın konu adı veya kendi parmak izi benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="56624-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="56624-127">bir sertifika parmak izini belirlemek için bkz: nasıl [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="56624-127"> how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="56624-128">Aşağıdaki kod örneğinde [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) sertifikada özel anahtarı konumunu belirlemek için aracı `My` depolamak `CurrentUser` parmak izi ile `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="56624-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="56624-129">Hesabı belirleyin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altında çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="56624-129">Determine the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under.</span></span>  
  
         <span data-ttu-id="56624-130">Aşağıdaki tabloda hesabıyla ayrıntıları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] belirli bir senaryo için çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="56624-130">The following table details the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="56624-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="56624-131">Scenario</span></span>|<span data-ttu-id="56624-132">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="56624-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="56624-133">İstemci (konsol veya WinForms uygulama).</span><span class="sxs-lookup"><span data-stu-id="56624-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="56624-134">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="56624-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="56624-135">Kendini barındıran hizmet.</span><span class="sxs-lookup"><span data-stu-id="56624-135">Service that is self-hosted.</span></span>|<span data-ttu-id="56624-136">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="56624-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="56624-137">IIS 6. 0'barındırılan hizmeti ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="56624-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="56624-138">AĞ HİZMETİ</span><span class="sxs-lookup"><span data-stu-id="56624-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="56624-139">Hizmet barındırılan IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="56624-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="56624-140">Tarafından denetlenen `<processModel>` Machine.config dosyasındaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="56624-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="56624-141">ASPNET varsayılan hesaptır.</span><span class="sxs-lookup"><span data-stu-id="56624-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="56624-142">Hesap için özel anahtarı içeren dosyayı okuma erişimi verme, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cacls.exe gibi bir araç kullanarak çalışan altında.</span><span class="sxs-lookup"><span data-stu-id="56624-142">Grant read access to the file that contains the private key to the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="56624-143">Aşağıdaki kod örneği düzenlemeleri (/ E) vermek belirtilen dosya için erişim denetim listesi (ACL) (/ G) ağ hizmeti hesabının okuma (: R) dosyaya erişimi.</span><span class="sxs-lookup"><span data-stu-id="56624-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="56624-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56624-144">See Also</span></span>  
 [<span data-ttu-id="56624-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="56624-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="56624-146">Nasıl yapılır: bir sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="56624-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="56624-147">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="56624-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
