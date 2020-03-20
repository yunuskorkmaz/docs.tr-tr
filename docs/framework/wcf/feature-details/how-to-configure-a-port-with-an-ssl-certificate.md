---
title: 'Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185101"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="0bccb-102">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0bccb-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="0bccb-103">Aktarım güvenliğini kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfla birlikte kendi kendine barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, X.509 sertifikasına sahip bir bağlantı noktasını da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="0bccb-104">Kendi kendine barındırılan bir hizmet oluşturmuyorsanız, hizmetinizi Internet Bilgi Hizmetleri'nde (IIS) barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bccb-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="0bccb-105">Daha fazla bilgi için [HTTP Transport Security'ye](../../../../docs/framework/wcf/feature-details/http-transport-security.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="0bccb-106">Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0bccb-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="0bccb-107">Windows Server 2003 çalıştırıyorsanız, HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="0bccb-108">Windows Server 2003'te bu araç yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="0bccb-109">Daha fazla bilgi için [Bkz. Httpcfg Genel Bakış.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="0bccb-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="0bccb-110">[Windows Destek Araçları belgeleri,](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) Httpcfg.exe aracının sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bccb-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="0bccb-111">Windows Vista'yı çalıştırıyorsanız, zaten yüklü olan Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0bccb-112">Bilgisayarda depolanan sertifikaları değiştirmek için yönetim ayrıcalıkları gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="0bccb-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="0bccb-113">Bağlantı noktalarının nasıl yapılandırıldırıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="0bccb-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="0bccb-114">Windows Server 2003 veya Windows XP'de, aşağıdaki örnekte gösterildiği gibi **sorgu** ve **ssl** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="0bccb-115">Windows Vista'da, aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="0bccb-116">Sertifikanın parmak izini alma</span><span class="sxs-lookup"><span data-stu-id="0bccb-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="0bccb-117">İstemci kimlik doğrulaması amacı olan bir X.509 sertifikası bulmak için MMC sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="0bccb-118">Daha fazla bilgi için [bkz: MMC Snap-in ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="0bccb-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="0bccb-119">Sertifikanın parmak izine erişin.</span><span class="sxs-lookup"><span data-stu-id="0bccb-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="0bccb-120">Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="0bccb-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="0bccb-121">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="0bccb-122">Hexadecimal karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="0bccb-123">Bunu başarmanın bir yolu, metin düzenleyicisinin bul-değiştir özelliğini kullanmak ve her alanı boş bir karakterle değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="0bccb-124">SSL sertifikasını bağlantı noktası numarasına bağlama</span><span class="sxs-lookup"><span data-stu-id="0bccb-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="0bccb-125">Windows Server 2003 veya Windows XP'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Soketler Katmanı'ndaki (SSL) "set" modundaki HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="0bccb-126">Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0bccb-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="0bccb-127">**-i** anahtarında `IP`sözdizimi`port` vardır: ve sertifikayı bilgisayarın 8012 portuna ayarlaması için araca talimat verir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="0bccb-128">İsteğe bağlı olarak, numaradan önce gelen dört sıfır bilgisayarın gerçek IP adresiyle de değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="0bccb-129">**-h** anahtarı sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="0bccb-130">Windows Vista'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="0bccb-131">**Certhash** parametresi sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="0bccb-132">**ipport** parametresi IP adresini ve bağlantı noktasını belirtir ve açıklanan Httpcfg.exe aracının **-i** anahtarı gibi işlevler.</span><span class="sxs-lookup"><span data-stu-id="0bccb-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="0bccb-133">**Appid** parametresi, sahibi olan uygulamayı tanımlamak için kullanılabilecek bir GUID'dir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="0bccb-134">SSL sertifikasını bağlantı noktası numarasına bağlama ve istemci sertifikalarını destekleme</span><span class="sxs-lookup"><span data-stu-id="0bccb-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="0bccb-135">Windows Server 2003 veya Windows XP'de, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi httpCfg.exe'ye ek bir komut satırı parametresini geçirin.</span><span class="sxs-lookup"><span data-stu-id="0bccb-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="0bccb-136">**-f** anahtarı, n'nin `n` 1 ile 7 arasında bir sayı olduğu yerin sözdizimini vardır.</span><span class="sxs-lookup"><span data-stu-id="0bccb-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="0bccb-137">Önceki örnekte gösterildiği gibi 2 değeri, aktarım katmanında istemci sertifikaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bccb-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="0bccb-138">3 değeri istemci sertifikaları sağlar ve bu sertifikaları bir Windows hesabıyla eşler.</span><span class="sxs-lookup"><span data-stu-id="0bccb-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="0bccb-139">Diğer değerlerin davranışı için HttpCfg.exe Yardım'a bakın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="0bccb-140">Windows Vista'da, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı izleyin, ancak ek bir parametreyle birlikte.</span><span class="sxs-lookup"><span data-stu-id="0bccb-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="0bccb-141">Bir SSL sertifikasını bağlantı noktası numarasından silme</span><span class="sxs-lookup"><span data-stu-id="0bccb-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="0bccb-142">Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg.exe veya Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="0bccb-143">Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="0bccb-144">Windows Server 2003 veya Windows XP'de, **delete** ve **ssl** anahtar kelimeleriyle birlikte HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="0bccb-145">**-i** anahtarını kullanarak `IP`:`port` sayıyı ve **-h** anahtarını işaret etmek için parmak izini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0bccb-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="0bccb-146">Windows Vista'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bccb-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="0bccb-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bccb-147">Example</span></span>  

 <span data-ttu-id="0bccb-148">Aşağıdaki kod, güvenliği taşımak için sınıf kümesini kullanarak kendi kendine barındırılan bir hizmetin <xref:System.ServiceModel.WSHttpBinding> nasıl oluşturulurulur gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bccb-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="0bccb-149">Bir uygulama oluştururken, adresteki bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0bccb-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0bccb-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bccb-150">See also</span></span>

- [<span data-ttu-id="0bccb-151">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0bccb-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
