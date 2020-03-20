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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184903"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="0fe93-102">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0fe93-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="0fe93-103">X.509 sertifikasını Windows Communication Foundation (WCF) tarafından erişilebilir hale getirmek için uygulama kodunun sertifika deposu adını ve konumunu belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="0fe93-104">Bazı durumlarda, işlem kimliğinin X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyaya erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe93-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="0fe93-105">Bir sertifika deposunda X.509 sertifikasıyla ilişkili özel anahtarı elde etmek için WCF'nin bunu yapmak için izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="0fe93-106">Varsayılan olarak, sertifikanın özel anahtarına yalnızca sahibi ve Sistem hesabı erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="0fe93-107">X.509 sertifikalarını WCF için erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="0fe93-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="0fe93-108">WCF'nin çalıştırdığı hesaba X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyaya okuma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="0fe93-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="0fe93-109">WCF'nin X.509 sertifikası için özel anahtara okuma erişimi gerekip gerekmediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe93-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="0fe93-110">Aşağıdaki tabloda, X.509 sertifikası kullanırken özel bir anahtarın kullanılabilir olup olmadığı açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="0fe93-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="0fe93-111">X.509 sertifika kullanımı</span><span class="sxs-lookup"><span data-stu-id="0fe93-111">X.509 certificate use</span></span>|<span data-ttu-id="0fe93-112">Özel anahtar</span><span class="sxs-lookup"><span data-stu-id="0fe93-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="0fe93-113">Giden SOAP mesajını dijital olarak imzalıyorum.</span><span class="sxs-lookup"><span data-stu-id="0fe93-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="0fe93-114">Evet</span><span class="sxs-lookup"><span data-stu-id="0fe93-114">Yes</span></span>|  
        |<span data-ttu-id="0fe93-115">Gelen SOAP iletisinin imzasını doğrulama.</span><span class="sxs-lookup"><span data-stu-id="0fe93-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="0fe93-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="0fe93-116">No</span></span>|  
        |<span data-ttu-id="0fe93-117">Giden SOAP iletisi şifreleme.</span><span class="sxs-lookup"><span data-stu-id="0fe93-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="0fe93-118">Hayır</span><span class="sxs-lookup"><span data-stu-id="0fe93-118">No</span></span>|  
        |<span data-ttu-id="0fe93-119">Gelen SOAP iletisini çözme.</span><span class="sxs-lookup"><span data-stu-id="0fe93-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="0fe93-120">Evet</span><span class="sxs-lookup"><span data-stu-id="0fe93-120">Yes</span></span>|  
  
    2. <span data-ttu-id="0fe93-121">Sertifika deposunun konumunu ve adını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe93-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="0fe93-122">Sertifikanın depolandığı sertifika deposu, uygulama kodunda veya yapılandırmada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="0fe93-123">Örneğin, aşağıdaki örnekte sertifikanın adlı `CurrentUser` `My`sertifika deposunda bulunduğu belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="0fe93-124">Sertifikanın özel anahtarının [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracını kullanarak bilgisayarda nerede bulunduğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe93-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="0fe93-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika deposunun adını, sertifika deposunun konumunu ve sertifikayı benzersiz olarak tanımlayan bir şey gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="0fe93-126">Araç, sertifikanın özne adını veya parmak izini benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0fe93-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="0fe93-127">Sertifikanın parmak izini nasıl belirleyiniz hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)</span><span class="sxs-lookup"><span data-stu-id="0fe93-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="0fe93-128">Aşağıdaki kod örneği, `My` mağazadaki `CurrentUser` bir sertifikanın özel anahtarının konumunu belirlemek için [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0fe93-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="0fe93-129">WCF'nin altında çalışan hesabı belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe93-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="0fe93-130">Aşağıdaki tablo, WCF'nin belirli bir senaryo için çalıştırdığı hesabı ayrıntılarıyla açıklar.</span><span class="sxs-lookup"><span data-stu-id="0fe93-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="0fe93-131">Senaryo</span><span class="sxs-lookup"><span data-stu-id="0fe93-131">Scenario</span></span>|<span data-ttu-id="0fe93-132">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="0fe93-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="0fe93-133">İstemci (konsol veya WinForms uygulaması).</span><span class="sxs-lookup"><span data-stu-id="0fe93-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="0fe93-134">Şu anda kullanıcı oturum açtı.</span><span class="sxs-lookup"><span data-stu-id="0fe93-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="0fe93-135">Kendi kendine barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="0fe93-135">Service that is self-hosted.</span></span>|<span data-ttu-id="0fe93-136">Şu anda kullanıcı oturum açtı.</span><span class="sxs-lookup"><span data-stu-id="0fe93-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="0fe93-137">IIS 6.0 (Windows Server 2003) veya IIS 7.0 'de (Windows Vista) barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="0fe93-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="0fe93-138">AĞ HİzMETİ</span><span class="sxs-lookup"><span data-stu-id="0fe93-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="0fe93-139">IIS 5.X'te (Windows XP) barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="0fe93-139">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="0fe93-140">Machine.config dosyasındaki `<processModel>` öğe tarafından kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="0fe93-141">Varsayılan hesap ASPNET'tir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="0fe93-142">Icacls.exe gibi bir aracı kullanarak WCF'nin altında çalıştırdığı hesabın özel anahtarını içeren dosyaya okuma erişimi ver.</span><span class="sxs-lookup"><span data-stu-id="0fe93-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="0fe93-143">Aşağıdaki kod örneği, belirtilen dosyanın NETWORK SERVICE hesabına okuma (:R) dosyaya erişim hakkı vermesi için isteğe bağlı erişim kontrol listesini (DACL) yönetmelikle tir.</span><span class="sxs-lookup"><span data-stu-id="0fe93-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="0fe93-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fe93-144">See also</span></span>

- [<span data-ttu-id="0fe93-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="0fe93-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="0fe93-146">Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma</span><span class="sxs-lookup"><span data-stu-id="0fe93-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="0fe93-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="0fe93-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
