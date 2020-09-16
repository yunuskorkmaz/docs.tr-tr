---
title: 'Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
description: Bir bağlantı noktasını, bir X. 509.952 sertifikası ile birlikte kullanarak, bir şirket içinde barındırılan WCF hizmeti için, taşıma güvenliği kullanan WSHttpBinding sınıfına sahip bir bağlantı noktasını nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 619a893e0973f6691e32446d75f101201a0b6799
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556388"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="ec65e-103">Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec65e-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="ec65e-104">Aktarım güvenliği kullanan sınıfla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken <xref:System.ServiceModel.WSHttpBinding> , bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="ec65e-105">Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec65e-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="ec65e-106">Daha fazla bilgi için bkz. [http aktarım güvenliği](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ec65e-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="ec65e-107">Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec65e-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="ec65e-108">Windows Server 2003 çalıştırıyorsanız HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="ec65e-109">Windows Server 2003 ' de bu araç yüklüdür.</span><span class="sxs-lookup"><span data-stu-id="ec65e-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="ec65e-110">Daha fazla bilgi için bkz. [Httpcfg Overview](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="ec65e-110">For more information, see [Httpcfg Overview](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="ec65e-111">[Windows Destek Araçları belgeleri](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) Httpcfg.exe aracının sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec65e-111">The [Windows Support Tools documentation](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="ec65e-112">Windows Vista çalıştırıyorsanız, zaten yüklü olan Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ec65e-113">Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="ec65e-114">Bağlantı noktalarının nasıl yapılandırıldığını belirleme</span><span class="sxs-lookup"><span data-stu-id="ec65e-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="ec65e-115">Windows Server 2003 veya Windows XP 'de, aşağıdaki örnekte gösterildiği gibi, **sorgu** ve **SSL** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="ec65e-116">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi, geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="ec65e-117">Bir sertifikanın parmak izini al</span><span class="sxs-lookup"><span data-stu-id="ec65e-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="ec65e-118">İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="ec65e-119">Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="ec65e-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="ec65e-120">Sertifikanın parmak izine erişin.</span><span class="sxs-lookup"><span data-stu-id="ec65e-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="ec65e-121">Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ec65e-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="ec65e-122">Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="ec65e-123">Onaltılık karakterler arasındaki tüm boşlukları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="ec65e-124">Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="ec65e-125">Bir bağlantı noktası numarasına SSL sertifikası bağlama</span><span class="sxs-lookup"><span data-stu-id="ec65e-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="ec65e-126">Windows Server 2003 veya Windows XP 'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "ayarla" modunda HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="ec65e-127">Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec65e-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="ec65e-128">**-I** anahtarı sözdizimine sahiptir `IP` : `port` ve araca sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="ec65e-129">İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="ec65e-130">**-H** anahtarı, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="ec65e-131">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="ec65e-132">**Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="ec65e-133">**Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve işlevleri açıklanan Httpcfg.exe aracının **-ı** anahtarı gibi işlevlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="ec65e-134">**AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="ec65e-135">Bir bağlantı noktası numarasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme</span><span class="sxs-lookup"><span data-stu-id="ec65e-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="ec65e-136">Windows Server 2003 veya Windows XP 'de, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi HttpCfg.exe ek bir komut satırı parametresi geçirin.</span><span class="sxs-lookup"><span data-stu-id="ec65e-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="ec65e-137">**-F** anahtarı, `n` n 'nin 1 ile 7 arasında bir sayı olduğu sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="ec65e-138">2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ec65e-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="ec65e-139">3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="ec65e-140">Diğer değerlerin davranışı için HttpCfg.exe yardımına bakın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="ec65e-141">Windows Vista 'da, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="ec65e-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="ec65e-142">Bir bağlantı noktası numarasından SSL sertifikası silme</span><span class="sxs-lookup"><span data-stu-id="ec65e-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="ec65e-143">Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg.exe veya Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="ec65e-144">Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="ec65e-145">Windows Server 2003 veya Windows XP 'de, **Delete** ve **ssl** anahtar sözcükleriyle HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="ec65e-146">**-i** `IP` `port` Parmak izini belirtmek için: Number ve **-h** anahtarını belirtmek için-ı anahtarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="ec65e-147">Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec65e-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="ec65e-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec65e-148">Example</span></span>  

 <span data-ttu-id="ec65e-149">Aşağıdaki kod, bir kendi kendine barındırılan hizmetin <xref:System.ServiceModel.WSHttpBinding> Aktarım güvenliği için ayarlanmış sınıfını kullanarak nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec65e-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="ec65e-150">Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ec65e-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ec65e-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec65e-151">See also</span></span>

- [<span data-ttu-id="ec65e-152">HTTP Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ec65e-152">HTTP Transport Security</span></span>](http-transport-security.md)
