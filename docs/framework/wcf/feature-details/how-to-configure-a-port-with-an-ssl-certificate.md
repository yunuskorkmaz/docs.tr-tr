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
ms.openlocfilehash: 99a08c9714e8f8cef0c1c96ac7f890d163324b44
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095027"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="132fd-102">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="132fd-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="132fd-103">Aktarım güvenliği kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfıyla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="132fd-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="132fd-104">Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="132fd-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="132fd-105">Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="132fd-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="132fd-106">Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="132fd-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="132fd-107">Windows Server 2003 çalıştırıyorsanız, HttpCfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="132fd-108">Windows Server 2003 ' de bu araç yüklüdür.</span><span class="sxs-lookup"><span data-stu-id="132fd-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="132fd-109">Daha fazla bilgi için bkz. [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="132fd-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="132fd-110">[Windows Destek Araçları belgeleri](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) , Httpcfg. exe aracının sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="132fd-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="132fd-111">Windows Vista çalıştırıyorsanız, zaten yüklü olan Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="132fd-112">Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="132fd-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="132fd-113">Bağlantı noktalarının nasıl yapılandırıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="132fd-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="132fd-114">Windows Server 2003 veya Windows XP 'de, aşağıdaki örnekte gösterildiği gibi, **sorgu** ve **SSL** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="132fd-115">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="132fd-116">Bir sertifikanın parmak izini al</span><span class="sxs-lookup"><span data-stu-id="132fd-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="132fd-117">İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="132fd-118">Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="132fd-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="132fd-119">Sertifikanın parmak izine erişin.</span><span class="sxs-lookup"><span data-stu-id="132fd-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="132fd-120">Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="132fd-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="132fd-121">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="132fd-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="132fd-122">Onaltılık karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="132fd-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="132fd-123">Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="132fd-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="132fd-124">Bir bağlantı noktası numarasına SSL sertifikası bağlama</span><span class="sxs-lookup"><span data-stu-id="132fd-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="132fd-125">Windows Server 2003 veya Windows XP 'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "küme" modunda HttpCfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="132fd-126">Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.</span><span class="sxs-lookup"><span data-stu-id="132fd-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="132fd-127">**-I** anahtarı `IP`:`port` sözdizimine sahiptir ve aracı sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="132fd-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="132fd-128">İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="132fd-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="132fd-129">**-H** anahtarı, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="132fd-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="132fd-130">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="132fd-131">**Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="132fd-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="132fd-132">**Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve yalnızca ' i r. exe aracının **-ı** anahtarı gibi işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="132fd-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="132fd-133">**AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.</span><span class="sxs-lookup"><span data-stu-id="132fd-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="132fd-134">Bir bağlantı noktası numarasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme</span><span class="sxs-lookup"><span data-stu-id="132fd-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="132fd-135">Windows Server 2003 veya Windows XP 'de, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi, HttpCfg. exe ' ye ek bir komut satırı parametresi geçirin.</span><span class="sxs-lookup"><span data-stu-id="132fd-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="132fd-136">**-F** anahtarının, 1 ile 7 arasında bir sayı olduğu `n` söz dizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="132fd-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="132fd-137">2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="132fd-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="132fd-138">3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="132fd-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="132fd-139">Diğer değerlerin davranışı için bkz. HttpCfg. exe yardımı.</span><span class="sxs-lookup"><span data-stu-id="132fd-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="132fd-140">Windows Vista 'da, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="132fd-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="132fd-141">Bir bağlantı noktası numarasından SSL sertifikası silme</span><span class="sxs-lookup"><span data-stu-id="132fd-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="132fd-142">Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg. exe veya Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="132fd-143">Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="132fd-144">Windows Server 2003 veya Windows XP 'de, **Delete** ve **SSL** anahtar sözcükleriyle Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="132fd-145">Parmak izini belirtmek için `IP`:`port` Number ve **-h** anahtarını belirtmek için **-ı** anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="132fd-146">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="132fd-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="132fd-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="132fd-147">Example</span></span>  

 <span data-ttu-id="132fd-148">Aşağıdaki kod, aktarım güvenliği için ayarlanan <xref:System.ServiceModel.WSHttpBinding> sınıfı kullanılarak şirket içinde barındırılan bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="132fd-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="132fd-149">Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="132fd-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="132fd-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="132fd-150">See also</span></span>

- [<span data-ttu-id="132fd-151">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="132fd-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
