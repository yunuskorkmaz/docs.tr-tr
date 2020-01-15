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
ms.openlocfilehash: 1ea7680d092a4270b8c0969c50db8accf7c23d49
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963303"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="a48b0-102">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a48b0-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="a48b0-103">Aktarım güvenliği kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfıyla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="a48b0-104">Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a48b0-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="a48b0-105">Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="a48b0-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="a48b0-106">Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a48b0-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="a48b0-107">Windows Server 2003 veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]çalıştırıyorsanız, HttpCfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-107">If you are running Windows Server 2003 or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="a48b0-108">Windows Server 2003 ile bu araç yüklüdür.</span><span class="sxs-lookup"><span data-stu-id="a48b0-108">With Windows Server 2003 this tool is installed.</span></span> <span data-ttu-id="a48b0-109">[!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı [WINDOWS XP Service Pack 2 destek araçları](https://go.microsoft.com/fwlink/?LinkId=88606)' na yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a48b0-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="a48b0-110">Daha fazla bilgi için bkz. [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="a48b0-110">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="a48b0-111">[Windows Destek Araçları belgeleri](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) , Httpcfg. exe aracının sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a48b0-111">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="a48b0-112">Windows Vista çalıştırıyorsanız, zaten yüklü olan Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="a48b0-113">Bu konu, birkaç yordamın nasıl gerçekleştirileceğini açıklamaktadır:</span><span class="sxs-lookup"><span data-stu-id="a48b0-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="a48b0-114">Bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleme.</span><span class="sxs-lookup"><span data-stu-id="a48b0-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="a48b0-115">Bir sertifikanın parmak izini alma (aşağıdaki iki yordam için gereklidir).</span><span class="sxs-lookup"><span data-stu-id="a48b0-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="a48b0-116">Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama.</span><span class="sxs-lookup"><span data-stu-id="a48b0-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="a48b0-117">Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme.</span><span class="sxs-lookup"><span data-stu-id="a48b0-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="a48b0-118">Bir bağlantı noktası numarasından SSL sertifikası siliniyor.</span><span class="sxs-lookup"><span data-stu-id="a48b0-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="a48b0-119">Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="a48b0-120">Bağlantı noktalarının nasıl yapılandırıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="a48b0-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="a48b0-121">Windows Server 2003 veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]'de, aşağıdaki örnekte gösterildiği gibi, **sorgu** ve **SSL** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-121">In Windows Server 2003 or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="a48b0-122">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-122">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="a48b0-123">Bir sertifikanın parmak izini almak için</span><span class="sxs-lookup"><span data-stu-id="a48b0-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="a48b0-124">İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="a48b0-125">Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="a48b0-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="a48b0-126">Sertifikanın parmak izine erişin.</span><span class="sxs-lookup"><span data-stu-id="a48b0-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="a48b0-127">Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a48b0-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="a48b0-128">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="a48b0-129">Onaltılık karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="a48b0-130">Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="a48b0-131">Bir SSL sertifikasını bir bağlantı noktası numarasına bağlamak için</span><span class="sxs-lookup"><span data-stu-id="a48b0-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="a48b0-132">Windows Server 2003 veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "küme" modunda HttpCfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-132">In Windows Server 2003 or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="a48b0-133">Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a48b0-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="a48b0-134">**-I** anahtarı `IP`:`port` sözdizimine sahiptir ve aracı sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="a48b0-135">İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="a48b0-136">**-H** anahtarı, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="a48b0-137">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-137">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="a48b0-138">**Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="a48b0-139">**Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve yalnızca ' i r. exe aracının **-ı** anahtarı gibi işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="a48b0-140">**AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="a48b0-141">Bir bağlantı noktası numarasına bir SSL sertifikası bağlamak ve istemci sertifikalarını desteklemek için</span><span class="sxs-lookup"><span data-stu-id="a48b0-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="a48b0-142">Windows Server 2003 veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi, HttpCfg. exe ' ye ek bir komut satırı parametresi geçirin.</span><span class="sxs-lookup"><span data-stu-id="a48b0-142">In Windows Server 2003 or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="a48b0-143">**-F** anahtarının, 1 ile 7 arasında bir sayı olduğu `n` söz dizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="a48b0-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="a48b0-144">2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="a48b0-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="a48b0-145">3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="a48b0-146">Diğer değerlerin davranışı için bkz. HttpCfg. exe yardımı.</span><span class="sxs-lookup"><span data-stu-id="a48b0-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="a48b0-147">Windows Vista 'da, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="a48b0-147">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="a48b0-148">Bir bağlantı noktası numarasından bir SSL sertifikası silmek için</span><span class="sxs-lookup"><span data-stu-id="a48b0-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="a48b0-149">Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg. exe veya Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="a48b0-150">Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="a48b0-151">Windows Server 2003 veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]'de, **Delete** ve **SSL** anahtar sözcükleriyle Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-151">In Windows Server 2003 or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="a48b0-152">Parmak izini belirtmek için `IP`:`port` Number ve **-h** anahtarını belirtmek için **-ı** anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="a48b0-153">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a48b0-153">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="a48b0-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="a48b0-154">Example</span></span>  
 <span data-ttu-id="a48b0-155">Aşağıdaki kod, aktarım güvenliği için ayarlanan <xref:System.ServiceModel.WSHttpBinding> sınıfı kullanılarak şirket içinde barındırılan bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a48b0-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="a48b0-156">Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a48b0-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a48b0-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a48b0-157">See also</span></span>

- [<span data-ttu-id="a48b0-158">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a48b0-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
