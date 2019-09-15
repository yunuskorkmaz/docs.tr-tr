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
ms.openlocfilehash: 401371bf01a62a20f2834cb76df19d9ddaacf83d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972350"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="74555-102">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="74555-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="74555-103">X. 509.440 sertifikasını Windows Communication Foundation (WCF) erişilebilir hale getirmek için, uygulama kodunun sertifika depolama adını ve konumunu belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="74555-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="74555-104">Bazı durumlarda, işlem kimliğinin X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74555-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="74555-105">Bir sertifika deposundaki bir X. 509.440 sertifikasıyla ilişkili özel anahtarı almak için, WCF 'nin bunu yapması için izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74555-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="74555-106">Varsayılan olarak, yalnızca sahip ve sistem hesabı bir sertifikanın özel anahtarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="74555-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="74555-107">X. 509.440 sertifikalarını WCF 'ye erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="74555-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="74555-108">WCF 'nin, X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya okuma erişiminin çalıştığı hesaba izin verin.</span><span class="sxs-lookup"><span data-stu-id="74555-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="74555-109">WCF 'nin X. 509.952 sertifikası için özel anahtara okuma erişimi gerektirip gerektirmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="74555-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="74555-110">Aşağıdaki tabloda, bir X. 509.440 sertifikası kullanılırken özel bir anahtarın kullanılabilir olup olmadığı ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74555-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="74555-111">X. 509.440 sertifika kullanımı</span><span class="sxs-lookup"><span data-stu-id="74555-111">X.509 certificate use</span></span>|<span data-ttu-id="74555-112">Özel anahtar</span><span class="sxs-lookup"><span data-stu-id="74555-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="74555-113">Giden bir SOAP iletisini dijital olarak imzalama.</span><span class="sxs-lookup"><span data-stu-id="74555-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="74555-114">Evet</span><span class="sxs-lookup"><span data-stu-id="74555-114">Yes</span></span>|  
        |<span data-ttu-id="74555-115">Gelen SOAP iletisinin imzası doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="74555-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="74555-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="74555-116">No</span></span>|  
        |<span data-ttu-id="74555-117">Giden bir SOAP iletisi şifreleniyor.</span><span class="sxs-lookup"><span data-stu-id="74555-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="74555-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="74555-118">No</span></span>|  
        |<span data-ttu-id="74555-119">Gelen SOAP iletisinin şifresini çözme.</span><span class="sxs-lookup"><span data-stu-id="74555-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="74555-120">Evet</span><span class="sxs-lookup"><span data-stu-id="74555-120">Yes</span></span>|  
  
    2. <span data-ttu-id="74555-121">Sertifika depolama konumunu ve sertifikanın depolandığı adı saptayın.</span><span class="sxs-lookup"><span data-stu-id="74555-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="74555-122">Sertifikanın depolandığı sertifika depolama alanı, uygulama kodunda ya da yapılandırmada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="74555-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="74555-123">Örneğin, aşağıdaki örnek, sertifikanın adlı `CurrentUser` `My`sertifika deposunda bulunduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="74555-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="74555-124">Sertifika için özel anahtarın, [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracını kullanarak bilgisayarda bulunduğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="74555-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="74555-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı sertifika depolama adı, sertifika depolama konumu ve sertifikayı benzersiz olarak tanımlayan bir şeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="74555-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="74555-126">Araç, sertifikanın konu adını ya da parmak izini benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="74555-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="74555-127">Bir sertifikanın parmak izini belirleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir sertifikanın](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)parmak izini alın.</span><span class="sxs-lookup"><span data-stu-id="74555-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="74555-128">Aşağıdaki kod örneği, bir parmak izine `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`sahip içindeki `My` `CurrentUser` depodaki bir sertifika için özel anahtar konumunu tespit etmek üzere [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="74555-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="74555-129">WCF 'nin altında çalıştığı hesabı belirleme.</span><span class="sxs-lookup"><span data-stu-id="74555-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="74555-130">Aşağıdaki tabloda, belirli bir senaryo için WCF 'nin çalıştığı hesabın ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74555-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="74555-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="74555-131">Scenario</span></span>|<span data-ttu-id="74555-132">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="74555-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="74555-133">İstemci (konsol veya WinForms uygulaması).</span><span class="sxs-lookup"><span data-stu-id="74555-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="74555-134">Şu anda oturum açmış olan kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="74555-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="74555-135">Kendi kendine barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="74555-135">Service that is self-hosted.</span></span>|<span data-ttu-id="74555-136">Şu anda oturum açmış olan kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="74555-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="74555-137">IIS 6,0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7,0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]) içinde barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="74555-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="74555-138">AĞ HIZMETI</span><span class="sxs-lookup"><span data-stu-id="74555-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="74555-139">IIS 5. X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]) içinde barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="74555-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="74555-140">Machine. config `<processModel>` dosyasındaki öğesi tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="74555-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="74555-141">Varsayılan hesap ASPNET ' dir.</span><span class="sxs-lookup"><span data-stu-id="74555-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="74555-142">Icacls. exe gibi bir araç kullanarak WCF 'nin altında çalıştığı hesaba özel anahtarı içeren dosyaya okuma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="74555-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="74555-143">Aşağıdaki kod örneği, ağ HIZMETI hesabına dosyaya okuma (: R) erişimi vermek için belirtilen dosya için isteğe bağlı erişim denetimi listesini (DACL) düzenler.</span><span class="sxs-lookup"><span data-stu-id="74555-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="74555-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74555-144">See also</span></span>

- [<span data-ttu-id="74555-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="74555-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="74555-146">Nasıl yapılır: Bir sertifikanın parmak Izini alma</span><span class="sxs-lookup"><span data-stu-id="74555-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="74555-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="74555-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
