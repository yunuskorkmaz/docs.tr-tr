---
title: 'Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: cd13eae0a72ceaf5abfb93dfe84a53cfc3c8dec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493712"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="5f381-102">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5f381-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="5f381-103">Bir X.509 sertifikası Windows Communication Foundation (WCF) için erişilebilir olması için uygulama kodu sertifika depolama alanı adı ve konumu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f381-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="5f381-104">Bazı durumlarda, işlem kimliği, X.509 sertifikayla ilişkili özel anahtarı içeren dosyayı için erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f381-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="5f381-105">Bir sertifika deposunda bir X.509 sertifikası ile ilişkili özel anahtarı edinmek için WCF Bunu yapmak için izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f381-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="5f381-106">Varsayılan olarak, yalnızca sahibi ve sistem hesabı, bir sertifikanın özel anahtarı erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5f381-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="5f381-107">X.509 sertifikalarını WCF için erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="5f381-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="5f381-108">X.509 sertifikayla ilişkili özel anahtarı içeren dosyaya okuma erişimi hangi WCF altında çalıştığı hesabın verin.</span><span class="sxs-lookup"><span data-stu-id="5f381-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="5f381-109">WCF X.509 sertifikası özel anahtarına okuma erişimi gerektiren olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="5f381-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="5f381-110">Bir özel anahtar bir X.509 sertifikası kullanırken kullanılabilir olmalıdır yoksa aşağıdaki tabloda ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f381-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="5f381-111">X.509 sertifika kullan</span><span class="sxs-lookup"><span data-stu-id="5f381-111">X.509 certificate use</span></span>|<span data-ttu-id="5f381-112">Özel anahtar</span><span class="sxs-lookup"><span data-stu-id="5f381-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="5f381-113">Giden SOAP ileti dijital olarak imzalamak.</span><span class="sxs-lookup"><span data-stu-id="5f381-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="5f381-114">Evet</span><span class="sxs-lookup"><span data-stu-id="5f381-114">Yes</span></span>|  
        |<span data-ttu-id="5f381-115">Gelen bir SOAP iletisi imzası doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="5f381-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="5f381-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="5f381-116">No</span></span>|  
        |<span data-ttu-id="5f381-117">Giden SOAP ileti şifreleme.</span><span class="sxs-lookup"><span data-stu-id="5f381-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="5f381-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="5f381-118">No</span></span>|  
        |<span data-ttu-id="5f381-119">Gelen bir SOAP iletisi çözme.</span><span class="sxs-lookup"><span data-stu-id="5f381-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="5f381-120">Evet</span><span class="sxs-lookup"><span data-stu-id="5f381-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="5f381-121">Sertifikanın depolandığı adı ve sertifika deposu konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="5f381-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="5f381-122">Sertifikanın depolandığı sertifika deposu uygulama kodu veya yapılandırmasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5f381-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="5f381-123">Örneğin, aşağıdaki örnek sertifika bulunan belirtir `CurrentUser` adlı sertifika deposuna `My`.</span><span class="sxs-lookup"><span data-stu-id="5f381-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="5f381-124">Kullanarak, sertifikanın özel anahtarı bilgisayarda bulunduğu belirlemek [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="5f381-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="5f381-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika depolama alanı adı, sertifika deposu konumu ve sertifika benzersiz olarak tanımlayan bir şey gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f381-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="5f381-126">Aracı sertifikanın konu adı veya kendi parmak izi benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5f381-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="5f381-127">Bir sertifika parmak izini belirleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="5f381-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="5f381-128">Aşağıdaki kod örneğinde [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) sertifikada özel anahtarı konumunu belirlemek için aracı `My` depolamak `CurrentUser` parmak izi ile `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="5f381-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="5f381-129">WCF altında çalıştığı hesabın belirler.</span><span class="sxs-lookup"><span data-stu-id="5f381-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="5f381-130">Aşağıdaki tabloda, WCF, belirli bir senaryo için çalıştığı hesap ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f381-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="5f381-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="5f381-131">Scenario</span></span>|<span data-ttu-id="5f381-132">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="5f381-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="5f381-133">İstemci (konsol veya WinForms uygulama).</span><span class="sxs-lookup"><span data-stu-id="5f381-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="5f381-134">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="5f381-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="5f381-135">Kendini barındıran hizmet.</span><span class="sxs-lookup"><span data-stu-id="5f381-135">Service that is self-hosted.</span></span>|<span data-ttu-id="5f381-136">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="5f381-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="5f381-137">IIS 6. 0'barındırılan hizmeti ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5f381-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="5f381-138">AĞ HİZMETİ</span><span class="sxs-lookup"><span data-stu-id="5f381-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="5f381-139">Hizmet barındırılan IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5f381-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="5f381-140">Tarafından denetlenen `<processModel>` Machine.config dosyasındaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="5f381-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="5f381-141">ASPNET varsayılan hesaptır.</span><span class="sxs-lookup"><span data-stu-id="5f381-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="5f381-142">WCF altında cacls.exe gibi bir araç kullanarak çalıştıran hesaba özel anahtarı içeren dosyayı okuma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="5f381-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="5f381-143">Aşağıdaki kod örneği düzenlemeleri (/ E) vermek belirtilen dosya için erişim denetim listesi (ACL) (/ G) ağ hizmeti hesabının okuma (: R) dosyaya erişimi.</span><span class="sxs-lookup"><span data-stu-id="5f381-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="5f381-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f381-144">See Also</span></span>  
 [<span data-ttu-id="5f381-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="5f381-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="5f381-146">Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma</span><span class="sxs-lookup"><span data-stu-id="5f381-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="5f381-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="5f381-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
