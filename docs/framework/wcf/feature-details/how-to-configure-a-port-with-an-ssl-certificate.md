---
title: 'Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893307"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="5e69e-102">Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5e69e-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="5e69e-103">Aktarım güvenliği kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="5e69e-104">Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e69e-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="5e69e-105">Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="5e69e-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="5e69e-106">Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e69e-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="5e69e-107">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]çalıştırıyorsanız, Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="5e69e-108">Bu [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] araçla birlikte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="5e69e-109">İle [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı [Windows XP Service Pack 2 destek araçları](https://go.microsoft.com/fwlink/?LinkId=88606)' na indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e69e-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="5e69e-110">Daha fazla bilgi için bkz. [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="5e69e-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="5e69e-111">[Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) , Httpcfg. exe aracının sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5e69e-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="5e69e-112">Çalıştırıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], zaten yüklü olan Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="5e69e-113">Bu konu, birkaç yordamın nasıl gerçekleştirileceğini açıklamaktadır:</span><span class="sxs-lookup"><span data-stu-id="5e69e-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="5e69e-114">Bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleme.</span><span class="sxs-lookup"><span data-stu-id="5e69e-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="5e69e-115">Bir sertifikanın parmak izini alma (aşağıdaki iki yordam için gereklidir).</span><span class="sxs-lookup"><span data-stu-id="5e69e-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="5e69e-116">Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama.</span><span class="sxs-lookup"><span data-stu-id="5e69e-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="5e69e-117">Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme.</span><span class="sxs-lookup"><span data-stu-id="5e69e-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="5e69e-118">Bir bağlantı noktası numarasından SSL sertifikası siliniyor.</span><span class="sxs-lookup"><span data-stu-id="5e69e-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="5e69e-119">Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="5e69e-120">Bağlantı noktalarının nasıl yapılandırıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="5e69e-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="5e69e-121">Veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ' de, aşağıdaki örnekte gösterildiği gibi, sorgu ve SSL anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için Httpcfg. exe aracını kullanın. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e69e-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="5e69e-122">' [!INCLUDE[wv](../../../../includes/wv-md.md)]De, aşağıdaki örnekte gösterildiği gibi, geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="5e69e-123">Bir sertifikanın parmak izini almak için</span><span class="sxs-lookup"><span data-stu-id="5e69e-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="5e69e-124">İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="5e69e-125">Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)ile sertifikaları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="5e69e-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="5e69e-126">Sertifikanın parmak izine erişin.</span><span class="sxs-lookup"><span data-stu-id="5e69e-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="5e69e-127">Daha fazla bilgi için [nasıl yapılır: Bir sertifikanın](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)parmak izini alın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="5e69e-128">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="5e69e-129">Onaltılık karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="5e69e-130">Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="5e69e-131">Bir SSL sertifikasını bir bağlantı noktası numarasına bağlamak için</span><span class="sxs-lookup"><span data-stu-id="5e69e-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="5e69e-132">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "ayarla" modunda Httpcfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="5e69e-133">Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e69e-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="5e69e-134">**-I** anahtarı sözdizimine `IP`sahiptir:`port` ve araca sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="5e69e-135">İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="5e69e-136">**-H** anahtarı, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="5e69e-137">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="5e69e-138">**Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="5e69e-139">**Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve yalnızca ' i r. exe aracının **-ı** anahtarı gibi işlevleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="5e69e-140">**AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="5e69e-141">Bir bağlantı noktası numarasına bir SSL sertifikası bağlamak ve istemci sertifikalarını desteklemek için</span><span class="sxs-lookup"><span data-stu-id="5e69e-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="5e69e-142">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de, aktarım katmanında X. 509.952 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi, Httpcfg. exe ' ye ek bir komut satırı parametresi geçirin.</span><span class="sxs-lookup"><span data-stu-id="5e69e-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="5e69e-143">**-F** anahtarı, n 'nin `n` 1 ile 7 arasında bir sayı olduğu sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="5e69e-144">2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5e69e-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="5e69e-145">3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="5e69e-146">Diğer değerlerin davranışı için bkz. HttpCfg. exe yardımı.</span><span class="sxs-lookup"><span data-stu-id="5e69e-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="5e69e-147">' [!INCLUDE[wv](../../../../includes/wv-md.md)]De, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e69e-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="5e69e-148">Bir bağlantı noktası numarasından bir SSL sertifikası silmek için</span><span class="sxs-lookup"><span data-stu-id="5e69e-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="5e69e-149">Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg. exe veya Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="5e69e-150">Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="5e69e-151">Veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] içinde, DELETE ve SSL anahtar sözcükleriyle Httpcfg. exe aracını kullanın. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e69e-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="5e69e-152">Parmak izini belirtmek için `IP`:`port` Number ve **-h** anahtarını belirtmek için **-ı** anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="5e69e-153">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e69e-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="5e69e-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e69e-154">Example</span></span>  
 <span data-ttu-id="5e69e-155">Aşağıdaki kod, bir kendi kendine barındırılan hizmetin aktarım güvenliği için ayarlanmış <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e69e-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="5e69e-156">Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5e69e-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5e69e-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e69e-157">See also</span></span>

- [<span data-ttu-id="5e69e-158">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5e69e-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
