---
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: d27ee01636e37ac8f09c4f7dc497f14bfac1b0f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424120"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="6757a-102">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6757a-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="6757a-103">Bu örnek, istemci için X. 509v3 sertifika kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509v3 sertifikasını MSMQ üzerinden kullanarak sunucu kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6757a-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="6757a-104">İleti güvenliği bazen MSMQ deposundaki iletilerin şifrelenmesinin ve uygulamanın kendi ileti kimlik doğrulamasını gerçekleştirebileceği durumlarda daha da tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="6757a-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="6757a-105">Bu örnek, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="6757a-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="6757a-106">İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6757a-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6757a-107">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6757a-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6757a-108">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6757a-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6757a-109">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="6757a-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="6757a-110">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6757a-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="6757a-111">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6757a-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="6757a-112">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="6757a-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="6757a-113">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="6757a-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="6757a-114">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="6757a-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="6757a-115">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="6757a-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="6757a-116">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="6757a-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="6757a-117">Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.</span><span class="sxs-lookup"><span data-stu-id="6757a-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="6757a-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6757a-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6757a-119">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6757a-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6757a-120">Yolun MakeCert. exe ve FindPrivateKey. exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6757a-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="6757a-121">Örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6757a-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="6757a-122">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="6757a-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6757a-123">Örnek ile işiniz bittiğinde Cleanup. bat dosyasını çalıştırarak sertifikaları kaldırtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6757a-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="6757a-124">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6757a-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="6757a-125">\Service\bin. adresinden Service. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="6757a-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="6757a-126">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="6757a-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="6757a-127">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6757a-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="6757a-128">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6757a-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6757a-129">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6757a-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6757a-130">Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="6757a-131">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6757a-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="6757a-132">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="6757a-133">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="6757a-134">Sunucusunda `setup.bat service`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6757a-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="6757a-135">`setup.bat` `service` bağımsız değişkeniyle çalıştırmak, bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="6757a-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="6757a-136">Hizmetin Service. exe. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını `findValue` ( [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) göstermek için düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="6757a-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="6757a-137">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="6757a-138">İstemcisinde `setup.bat client`' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6757a-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="6757a-139">`setup.bat` `client` bağımsız değişkeniyle çalıştırmak, client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="6757a-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="6757a-140">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6757a-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="6757a-141">Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="6757a-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="6757a-142">Ayrıca hizmetin sertifika adını, hizmet bilgisayarının tam etki alanı adıyla aynı olacak şekilde değiştirmeniz gerekir (`clientCredentials`altında `serviceCertificate` `defaultCertificate` öğesindeki `findValue` özniteliğinde).</span><span class="sxs-lookup"><span data-stu-id="6757a-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="6757a-143">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="6757a-144">İstemcisinde `ImportServiceCert.bat`' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6757a-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="6757a-145">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="6757a-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="6757a-146">Sunucusunda `ImportClientCert.bat`çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="6757a-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="6757a-147">Hizmet bilgisayarında, komut isteminden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="6757a-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="6757a-148">İstemci bilgisayarda, komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="6757a-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="6757a-149">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6757a-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6757a-150">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="6757a-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="6757a-151">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6757a-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6757a-152">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="6757a-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="6757a-153">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6757a-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="6757a-154">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="6757a-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6757a-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6757a-155">Requirements</span></span>
 <span data-ttu-id="6757a-156">Bu örnek, MSMQ 'nun yüklü ve çalışıyor olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6757a-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6757a-157">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="6757a-157">Demonstrates</span></span>
 <span data-ttu-id="6757a-158">İstemci, hizmetin ortak anahtarını kullanarak iletiyi şifreler ve kendi sertifikasını kullanarak iletiyi imzalar.</span><span class="sxs-lookup"><span data-stu-id="6757a-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="6757a-159">Sıradan iletiyi okuyan hizmet, güvenilen kişiler deposundaki sertifikayla istemci sertifikasının kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="6757a-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="6757a-160">Daha sonra iletinin şifresini çözer ve iletiyi hizmet işlemine gönderir.</span><span class="sxs-lookup"><span data-stu-id="6757a-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="6757a-161">Windows Communication Foundation (WCF) iletisi MSMQ iletisinin gövdesinde bir yük olarak yapıldığından, gövde MSMQ deposunda şifreli olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="6757a-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="6757a-162">Bu, iletinin istenmeyen açıklanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6757a-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="6757a-163">MSMQ 'nun, taşıma işlemi yaptığı İletinin şifrelenip şifrelenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="6757a-164">Örnek, ileti düzeyindeki karşılıklı kimlik doğrulamanın MSMQ ile nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6757a-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="6757a-165">Sertifikalar bant dışı olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="6757a-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="6757a-166">Hizmet ve istemcinin aynı anda çalışmaya ve çalışır durumda olmaması gerektiğinden, bu her zaman kuyruğa alınmış uygulama ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6757a-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="6757a-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6757a-167">Description</span></span>
 <span data-ttu-id="6757a-168">Örnek istemci ve hizmet kodu, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğiyle tek bir farklılık ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6757a-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="6757a-169">İşlem sözleşmesine, iletinin imzalanması ve şifrelenmesi gerektiğini öneren koruma düzeyiyle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="6757a-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="6757a-170">Hizmeti ve istemciyi tanımlamak için gereken belirteç kullanılarak iletinin güvenli olduğundan emin olmak için, App. config kimlik bilgisi bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6757a-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="6757a-171">İstemci yapılandırması, hizmetin kimliğini doğrulamak için hizmet sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6757a-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="6757a-172">Hizmetin geçerliliğini sağlamak için, güvenli depo olarak kendi LocalMachine mağazasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6757a-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="6757a-173">Ayrıca, istemcinin hizmet kimlik doğrulaması için iletiyle ilişkili istemci sertifikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="6757a-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="6757a-174">Güvenlik modunun Ileti olarak ayarlandığını ve ClientCredentialType 'un sertifika olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6757a-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="6757a-175">Hizmet yapılandırması, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışı içerir.</span><span class="sxs-lookup"><span data-stu-id="6757a-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="6757a-176">Sunucu sertifikası konu adı, [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)`findValue` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6757a-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="6757a-177">Örnek, yapılandırma kullanarak kimlik doğrulamanın denetlenmesini ve aşağıdaki örnek kodda gösterildiği gibi çağıranın kimliğini güvenlik bağlamında nasıl elde leyeceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="6757a-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="6757a-178">Çalıştırıldığında, hizmet kodu istemci kimliğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6757a-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="6757a-179">Aşağıda, hizmet kodundan alınan bir örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6757a-179">The following is a sample output from the service code:</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="6757a-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6757a-180">Comments</span></span>

- <span data-ttu-id="6757a-181">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="6757a-181">Creating the client certificate.</span></span>

     <span data-ttu-id="6757a-182">Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6757a-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="6757a-183">Belirtilen istemci adı, oluşturulan sertifikanın konu adı ' nda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6757a-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="6757a-184">Sertifika, `CurrentUser` depolama konumunda `My` deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="6757a-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6757a-185">İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="6757a-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="6757a-186">Toplu iş dosyasında aşağıdaki satır, sunucunun ilgili güveni veya güven dışı kararlar verebilmeleri için istemci sertifikasını sunucunun Trustedkişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6757a-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="6757a-187">Trustedkişiler deposuna bir Windows Communication Foundation (WCF) hizmeti tarafından Güvenilmeye yönelik bir sertifika için, istemci sertifikası doğrulama modunun `PeerOrChainTrust` veya `PeerTrust` değeri olarak ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6757a-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="6757a-188">Bunun bir yapılandırma dosyası kullanılarak nasıl yapılabileceğinizi öğrenmek için önceki hizmet yapılandırma örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="6757a-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="6757a-189">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="6757a-189">Creating the server certificate.</span></span>

     <span data-ttu-id="6757a-190">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6757a-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="6757a-191">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="6757a-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="6757a-192">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="6757a-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="6757a-193">Kurulum Batch dosyası bir hizmet bağımsız değişkeniyle (örneğin, `setup.bat service`) çalışıyorsa% SUNUCU_ADı% bilgisayarın tam etki alanı adını içerir. Aksi takdirde, varsayılan olarak localhost olur</span><span class="sxs-lookup"><span data-stu-id="6757a-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="6757a-194">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="6757a-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="6757a-195">Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="6757a-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6757a-196">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6757a-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6757a-197">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6757a-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="6757a-198">Microsoft Windows 'un U. S. Ingilizce sürümünü kullanıyorsanız, Setup. bat dosyasını düzenlemeniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6757a-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6757a-199">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6757a-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6757a-200">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6757a-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6757a-201">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="6757a-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6757a-202">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6757a-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
