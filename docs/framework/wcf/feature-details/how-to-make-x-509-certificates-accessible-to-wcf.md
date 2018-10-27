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
ms.openlocfilehash: 0917569b556c31413b715d75c83a96f3a4b015d7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192206"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="8a9af-102">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8a9af-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="8a9af-103">X.509 sertifikası Windows Communication Foundation (WCF) için erişilebilir hale getirmek için uygulama kodu, sertifika deposu adını ve konumunu belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9af-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="8a9af-104">Bazı durumlarda, işlem kimliği X.509 sertifikası ile ilişkili özel anahtarı içeren dosyayı erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a9af-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="8a9af-105">Bir sertifika deposunda X.509 sertifikası ile ilişkili özel anahtarı almak için WCF, bunu yapmak için izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a9af-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="8a9af-106">Varsayılan olarak, bir sertifikanın özel anahtarı yalnızca sahibi ve System hesabıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9af-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="8a9af-107">X.509 sertifikalarını WCF için erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8a9af-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="8a9af-108">X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyayı için okuma erişimi hangi WCF altında çalıştığı hesabın verin.</span><span class="sxs-lookup"><span data-stu-id="8a9af-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="8a9af-109">WCF için X.509 sertifikası özel anahtarı için okuma erişimi gerekli olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8a9af-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="8a9af-110">Aşağıdaki tabloda, özel anahtarı kullanarak bir X.509 sertifikası olduğunda kullanılabilir olmalıdır yoksa ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="8a9af-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="8a9af-111">X.509 sertifika kullan</span><span class="sxs-lookup"><span data-stu-id="8a9af-111">X.509 certificate use</span></span>|<span data-ttu-id="8a9af-112">özel anahtar</span><span class="sxs-lookup"><span data-stu-id="8a9af-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="8a9af-113">Giden SOAP ileti imzalamak.</span><span class="sxs-lookup"><span data-stu-id="8a9af-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="8a9af-114">Evet</span><span class="sxs-lookup"><span data-stu-id="8a9af-114">Yes</span></span>|  
        |<span data-ttu-id="8a9af-115">Gelen bir SOAP ileti imzası doğrulama.</span><span class="sxs-lookup"><span data-stu-id="8a9af-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="8a9af-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="8a9af-116">No</span></span>|  
        |<span data-ttu-id="8a9af-117">Giden SOAP ileti şifreleme.</span><span class="sxs-lookup"><span data-stu-id="8a9af-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="8a9af-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="8a9af-118">No</span></span>|  
        |<span data-ttu-id="8a9af-119">Gelen bir SOAP iletisi şifre çözme.</span><span class="sxs-lookup"><span data-stu-id="8a9af-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="8a9af-120">Evet</span><span class="sxs-lookup"><span data-stu-id="8a9af-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="8a9af-121">Sertifikanın depolandığı adı ve sertifika depo konumunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8a9af-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="8a9af-122">Sertifika deposuna sertifikanın depolandığı, uygulama kodu veya yapılandırmada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8a9af-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="8a9af-123">Örneğin, aşağıdaki örnekte sertifika bulunan belirtir `CurrentUser` adlı sertifika deposuna `My`.</span><span class="sxs-lookup"><span data-stu-id="8a9af-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="8a9af-124">Kullanarak, sertifika özel anahtarını bilgisayarda nerede belirlemek [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="8a9af-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="8a9af-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika deposunun adını, sertifika depo konumunu ve sertifika benzersiz olarak tanımlayan bir şey gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a9af-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="8a9af-126">Aracı sertifikanın konu adı veya parmak izi benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8a9af-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="8a9af-127">Bir sertifika parmak izini belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8a9af-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="8a9af-128">Aşağıdaki kod örneğinde [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) için sertifikada özel anahtar konumunu belirlemek için aracı `My` depolar `CurrentUser` parmak izi ile `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="8a9af-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="8a9af-129">WCF altında çalıştığı hesabı belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8a9af-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="8a9af-130">Aşağıdaki tabloda, WCF, belirli bir senaryo için çalıştığı hesabı ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="8a9af-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="8a9af-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="8a9af-131">Scenario</span></span>|<span data-ttu-id="8a9af-132">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="8a9af-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="8a9af-133">İstemci (konsol veya aplikace WinForms).</span><span class="sxs-lookup"><span data-stu-id="8a9af-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="8a9af-134">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="8a9af-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="8a9af-135">Şirket içinde barındırılan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="8a9af-135">Service that is self-hosted.</span></span>|<span data-ttu-id="8a9af-136">Şu anda oturum açmış kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="8a9af-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="8a9af-137">IIS 6. 0'barındırılan hizmeti ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="8a9af-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="8a9af-138">AĞ HİZMETİ</span><span class="sxs-lookup"><span data-stu-id="8a9af-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="8a9af-139">Hizmet barındırılan IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="8a9af-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="8a9af-140">Denetlenen `<processModel>` Machine.config dosyasında öğe.</span><span class="sxs-lookup"><span data-stu-id="8a9af-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="8a9af-141">ASP.NET varsayılan hesaptır.</span><span class="sxs-lookup"><span data-stu-id="8a9af-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="8a9af-142">WCF altında icacls.exe gibi bir araç kullanarak çalıştıran hesaba özel anahtarı içeren dosyayı okuma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="8a9af-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="8a9af-143">Aşağıdaki kod örneği, ağ hizmeti hesabı okuma izni belirtilen dosya için isteğe bağlı erişim denetimi listesini (DACL) düzenler (: R) dosyasına erişim.</span><span class="sxs-lookup"><span data-stu-id="8a9af-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="8a9af-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a9af-144">See Also</span></span>  
- [<span data-ttu-id="8a9af-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="8a9af-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
- [<span data-ttu-id="8a9af-146">Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma</span><span class="sxs-lookup"><span data-stu-id="8a9af-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
- [<span data-ttu-id="8a9af-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="8a9af-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
