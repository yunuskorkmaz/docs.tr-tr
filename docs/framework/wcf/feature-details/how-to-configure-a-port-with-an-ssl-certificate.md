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
ms.openlocfilehash: d709123895f361c1d2268a218b4163c8d195e1b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047972"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="efff6-102">Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="efff6-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="efff6-103">Şirket içinde barındırılan Windows Communication Foundation (WCF) hizmet ile oluşturulurken <xref:System.ServiceModel.WSHttpBinding> sınıfı bu kullanımları aktarım güvenliği, ayrıca bir X.509 sertifikası ile bir bağlantı noktası yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="efff6-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="efff6-104">Şirket içinde barındırılan bir hizmet oluşturmuyorsanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efff6-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="efff6-105">Daha fazla bilgi için [HTTP aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="efff6-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="efff6-106">Bir bağlantı noktasını yapılandırmak için kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="efff6-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="efff6-107">Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="efff6-108">İle [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] bu aracı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="efff6-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="efff6-109">İle [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı indirebileceğiniz [Windows XP Service Pack 2 Destek Araçları](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="efff6-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="efff6-110">Daha fazla bilgi için [Httpcfg genel bakış](https://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="efff6-110">For more information, see [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="efff6-111">[Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) Httpcfg.exe aracın sözdizimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="efff6-111">The [Windows Support Tools documentation](https://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="efff6-112">Çalıştırıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], zaten yüklü Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="efff6-113">Bu konuda çeşitli yordamları nasıl yapılacağını anlatmaktadır:</span><span class="sxs-lookup"><span data-stu-id="efff6-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="efff6-114">Bir bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleniyor.</span><span class="sxs-lookup"><span data-stu-id="efff6-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="efff6-115">Bir sertifikanın parmak izi (aşağıdaki iki yordamdan için gerekli) alma.</span><span class="sxs-lookup"><span data-stu-id="efff6-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="efff6-116">Bir bağlantı noktası yapılandırması için bir SSL sertifikası bağlama.</span><span class="sxs-lookup"><span data-stu-id="efff6-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="efff6-117">Bir bağlantı noktası yapılandırması ve istemci sertifikalarını destekleyen bir SSL sertifikası bağlama.</span><span class="sxs-lookup"><span data-stu-id="efff6-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="efff6-118">Bir bağlantı noktası numarasından bir SSL sertifikası siliniyor.</span><span class="sxs-lookup"><span data-stu-id="efff6-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="efff6-119">Bilgisayarda depolanan sertifikaları değiştirme yönetici ayrıcalıklarını gerektirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="efff6-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="efff6-120">Bağlantı noktalarını nasıl yapılandırılacağını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="efff6-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="efff6-121">İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe geçerli bağlantı noktası yapılandırmasını görüntülemek için aracını kullanarak **sorgu** ve **ssl** geçer, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="efff6-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="efff6-122">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi geçerli bir bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="efff6-123">Bir sertifikanın parmak izi almak için</span><span class="sxs-lookup"><span data-stu-id="efff6-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="efff6-124">İstemci kimlik doğrulaması amacı olan bir X.509 sertifikası bulunamıyor sertifikalar MMC ek bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="efff6-125">Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="efff6-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="efff6-126">Sertifikanın parmak izi erişin.</span><span class="sxs-lookup"><span data-stu-id="efff6-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="efff6-127">Daha fazla bilgi için [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="efff6-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="efff6-128">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="efff6-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="efff6-129">Onaltılık karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="efff6-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="efff6-130">Bunu gerçekleştirmek için bir metin Düzenleyicisi'nin Bul ve Değiştir özelliğini kullanın ve her alanı null karakteri ile değiştirmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="efff6-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="efff6-131">Bir bağlantı noktası numarası için bir SSL sertifikası bağlamak için</span><span class="sxs-lookup"><span data-stu-id="efff6-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="efff6-132">İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], sertifikayı bir bağlantı noktası numarasını bağlamak için "Ayarla" modunda Güvenli Yuva Katmanı (SSL) deposunda HttpCfg.exe Aracı'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="efff6-133">Aracı parmak izi sertifika tanımlamak için aşağıdaki örnekte gösterildiği gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="efff6-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="efff6-134">**-İ** anahtar söz dizimi olan `IP`:`port` ve bilgisayarın 8012 bağlantı için sertifika ayarlamak için araç bildirir.</span><span class="sxs-lookup"><span data-stu-id="efff6-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="efff6-135">İsteğe bağlı olarak, sayı önünde dört sıfırları bilgisayarın gerçek IP adresine göre değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="efff6-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="efff6-136">**-H** anahtar sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efff6-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="efff6-137">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="efff6-138">**Certhash** parametresi, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efff6-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="efff6-139">**İpport** parametresi, IP adresi ve bağlantı noktasını belirtir ve işlevleri olduğu gibi **-i** açıklanan Httpcfg.exe Aracı'nın anahtarı.</span><span class="sxs-lookup"><span data-stu-id="efff6-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="efff6-140">**AppID** parametredir sahip olan uygulamayı tanımlamak için kullanılan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="efff6-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="efff6-141">Bir bağlantı noktası numarası için bir SSL sertifikası bağlama ve istemci sertifikalarını desteklemek için</span><span class="sxs-lookup"><span data-stu-id="efff6-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="efff6-142">İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aktarım katmanında X.509 sertifikalarıyla kimlik doğrulaması için yukarıdaki yordamı izleyin ancak aşağıdaki örnekte gösterildiği gibi bir ek komut satırı parametresi HttpCfg.exe için geçmesi istemcileri desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="efff6-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="efff6-143">**-F** anahtar söz dizimi olan `n` burada n, 1 ile 7 arasında bir sayı.</span><span class="sxs-lookup"><span data-stu-id="efff6-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="efff6-144">Değeri 2 ' nin, istemci sertifikaları aktarım katmanında önceki örnekte gösterilen şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="efff6-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="efff6-145">3 değeri, istemci sertifikaları sağlar ve bu sertifikaları için bir Windows hesabı eşler.</span><span class="sxs-lookup"><span data-stu-id="efff6-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="efff6-146">Diğer değerleri davranışı için HttpCfg.exe yardımına bakın.</span><span class="sxs-lookup"><span data-stu-id="efff6-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="efff6-147">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], yukarıdaki yordamı izleyin, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulaması istemcileri destekler, ancak aşağıdaki örnekte gösterildiği gibi ek bir parametre.</span><span class="sxs-lookup"><span data-stu-id="efff6-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="efff6-148">Bir bağlantı noktası numarasından bir SSL sertifikası silinemedi</span><span class="sxs-lookup"><span data-stu-id="efff6-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="efff6-149">Bilgisayarda tüm bağlamaları parmak izleriyle ve bağlantı noktalarını görmek için HttpCfg.exe veya Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="efff6-150">Disk bilgileri yazdırmak için yeniden yönlendirme karakter kullanın ">" aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="efff6-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. <span data-ttu-id="efff6-151">İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını **Sil** ve **ssl** anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="efff6-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="efff6-152">Kullanım **-i** belirlemek için anahtarı `IP`:`port` numarası ve **-h** parmak izini belirlemek için anahtarı.</span><span class="sxs-lookup"><span data-stu-id="efff6-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="efff6-153">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="efff6-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="efff6-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="efff6-154">Example</span></span>  
 <span data-ttu-id="efff6-155">Aşağıdaki kodu kullanarak bir şirket içinde barındırılan hizmeti oluşturulacağını gösterir <xref:System.ServiceModel.WSHttpBinding> aktarım güvenliği kümesine sınıfı.</span><span class="sxs-lookup"><span data-stu-id="efff6-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="efff6-156">Bir uygulama oluştururken, adres, bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="efff6-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="efff6-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efff6-157">See also</span></span>

- [<span data-ttu-id="efff6-158">HTTP Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="efff6-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
