---
description: 'Hakkında daha fazla bilgi edinin: Message Queuing üzerinde Ileti güvenliği'
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: bfbec02dec11d4f4eb153db942eb12ce4cb595e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752333"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="c4b56-103">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c4b56-103">Message Security over Message Queuing</span></span>

<span data-ttu-id="c4b56-104">Bu örnek, istemci için X. 509v3 sertifika kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509v3 sertifikasını MSMQ üzerinden kullanarak sunucu kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-104">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="c4b56-105">İleti güvenliği bazen MSMQ deposundaki iletilerin şifrelenmesinin ve uygulamanın kendi ileti kimlik doğrulamasını gerçekleştirebileceği durumlarda daha da tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-105">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="c4b56-106">Bu örnek, [IŞLENEN MSMQ bağlama](transacted-msmq-binding.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-106">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="c4b56-107">İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-107">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4b56-108">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4b56-108">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c4b56-109">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4b56-109">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c4b56-110">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-110">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c4b56-111">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4b56-111">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c4b56-112">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4b56-112">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c4b56-113">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-113">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="c4b56-114">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-114">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="c4b56-115">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-115">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="c4b56-116">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-116">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="c4b56-117">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-117">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="c4b56-118">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-118">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="c4b56-119">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c4b56-120">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4b56-120">To run the sample on the same computer</span></span>

1. <span data-ttu-id="c4b56-121">Yolun Makecert.exe ve FindPrivateKey.exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4b56-121">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="c4b56-122">Örnek yüklemesi klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-122">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="c4b56-123">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="c4b56-123">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c4b56-124">Örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4b56-124">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="c4b56-125">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-125">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="c4b56-126">\Service\bin. 'den başlatma Service.exe</span><span class="sxs-lookup"><span data-stu-id="c4b56-126">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="c4b56-127">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="c4b56-127">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c4b56-128">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-128">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="c4b56-129">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c4b56-129">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c4b56-130">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4b56-130">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="c4b56-131">Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-131">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="c4b56-132">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4b56-132">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="c4b56-133">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-133">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c4b56-134">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-134">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="c4b56-135">Sunucusunda öğesini çalıştırın `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-135">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="c4b56-136">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-136">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="c4b56-137">Hizmetin service.exe.config `findValue` , [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-137">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="c4b56-138">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-138">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="c4b56-139">İstemcisinde öğesini çalıştırın `setup.bat client` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-139">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="c4b56-140">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` Client.com adlı bir istemci sertifikası oluşturur ve Istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-140">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="c4b56-141">İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-141">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c4b56-142">Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-142">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="c4b56-143">Ayrıca hizmetin sertifika adını, hizmet bilgisayarının tam etki alanı adıyla aynı olacak şekilde değiştirmeniz gerekir ( `findValue` `defaultCertificate` altındaki öğesinde özniteliğinde `serviceCertificate` `clientCredentials` ).</span><span class="sxs-lookup"><span data-stu-id="c4b56-143">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="c4b56-144">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-144">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="c4b56-145">İstemcisinde öğesini çalıştırın `ImportServiceCert.bat` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-145">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="c4b56-146">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-146">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="c4b56-147">Sunucusunda, `ImportClientCert.bat` Bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-147">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="c4b56-148">Hizmet bilgisayarında, komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-148">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="c4b56-149">İstemci bilgisayarda, komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-149">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="c4b56-150">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c4b56-150">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c4b56-151">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="c4b56-151">To clean up after the sample</span></span>  
  
- <span data-ttu-id="c4b56-152">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-152">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c4b56-153">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="c4b56-153">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c4b56-154">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4b56-154">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c4b56-155">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-155">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4b56-156">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4b56-156">Requirements</span></span>

 <span data-ttu-id="c4b56-157">Bu örnek, MSMQ 'nun yüklü ve çalışıyor olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-157">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c4b56-158">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="c4b56-158">Demonstrates</span></span>

 <span data-ttu-id="c4b56-159">İstemci, hizmetin ortak anahtarını kullanarak iletiyi şifreler ve kendi sertifikasını kullanarak iletiyi imzalar.</span><span class="sxs-lookup"><span data-stu-id="c4b56-159">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="c4b56-160">Sıradan iletiyi okuyan hizmet, güvenilen kişiler deposundaki sertifikayla istemci sertifikasının kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="c4b56-160">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="c4b56-161">Daha sonra iletinin şifresini çözer ve iletiyi hizmet işlemine gönderir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-161">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="c4b56-162">Windows Communication Foundation (WCF) iletisi MSMQ iletisinin gövdesinde bir yük olarak yapıldığından, gövde MSMQ deposunda şifreli olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-162">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="c4b56-163">Bu, iletinin istenmeyen açıklanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4b56-163">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="c4b56-164">MSMQ 'nun, taşıma işlemi yaptığı İletinin şifrelenip şifrelenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-164">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="c4b56-165">Örnek, ileti düzeyindeki karşılıklı kimlik doğrulamanın MSMQ ile nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-165">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="c4b56-166">Sertifikalar bant dışı olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-166">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="c4b56-167">Hizmet ve istemcinin aynı anda çalışmaya ve çalışır durumda olmaması gerektiğinden, bu her zaman kuyruğa alınmış uygulama ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-167">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="c4b56-168">Description</span><span class="sxs-lookup"><span data-stu-id="c4b56-168">Description</span></span>

 <span data-ttu-id="c4b56-169">Örnek istemci ve hizmet kodu, [IŞLENEN MSMQ bağlama](transacted-msmq-binding.md) örneğiyle tek bir farklılık ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-169">The sample client and service code are the same as the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="c4b56-170">İşlem sözleşmesine, iletinin imzalanması ve şifrelenmesi gerektiğini öneren koruma düzeyiyle açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-170">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="c4b56-171">Hizmetin, hizmeti ve istemciyi tanımlamak için gereken belirteç kullanılarak güvenli olduğundan emin olmak için, App.config kimlik bilgisi bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-171">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="c4b56-172">İstemci yapılandırması, hizmetin kimliğini doğrulamak için hizmet sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-172">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="c4b56-173">Hizmetin geçerliliğini sağlamak için, güvenli depo olarak kendi LocalMachine mağazasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-173">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="c4b56-174">Ayrıca, istemcinin hizmet kimlik doğrulaması için iletiyle ilişkili istemci sertifikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-174">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="c4b56-175">Güvenlik modunun Ileti olarak ayarlandığını ve ClientCredentialType 'un sertifika olarak ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-175">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="c4b56-176">Hizmet yapılandırması, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışı içerir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-176">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="c4b56-177">Sunucu sertifikası konu adı `findValue` , içindeki özniteliğinde belirtilir [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="c4b56-177">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="c4b56-178">Örnek, yapılandırma kullanarak kimlik doğrulamanın denetlenmesini ve aşağıdaki örnek kodda gösterildiği gibi çağıranın kimliğini güvenlik bağlamında nasıl elde leyeceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="c4b56-178">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="c4b56-179">Çalıştırıldığında, hizmet kodu istemci kimliğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c4b56-179">When run, the service code displays the client identification.</span></span> <span data-ttu-id="c4b56-180">Aşağıda, hizmet kodundan alınan bir örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c4b56-180">The following is a sample output from the service code:</span></span>

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

## <a name="comments"></a><span data-ttu-id="c4b56-181">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="c4b56-181">Comments</span></span>

- <span data-ttu-id="c4b56-182">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c4b56-182">Creating the client certificate.</span></span>

     <span data-ttu-id="c4b56-183">Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4b56-183">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="c4b56-184">Belirtilen istemci adı, oluşturulan sertifikanın konu adı ' nda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-184">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="c4b56-185">Sertifika mağaza `My` konumunda mağaza 'da depolanır `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-185">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="c4b56-186">İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="c4b56-186">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="c4b56-187">Toplu iş dosyasında aşağıdaki satır, sunucunun ilgili güveni veya güven dışı kararlar verebilmeleri için istemci sertifikasını sunucunun Trustedkişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c4b56-187">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="c4b56-188">Trustedkişiler deposuna bir Windows Communication Foundation (WCF) hizmeti tarafından Güvenilmeye yönelik bir sertifika için, istemci sertifikası doğrulama modunun veya değeri olarak ayarlanması gerekir `PeerOrChainTrust` `PeerTrust` .</span><span class="sxs-lookup"><span data-stu-id="c4b56-188">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="c4b56-189">Bunun bir yapılandırma dosyası kullanılarak nasıl yapılabileceğinizi öğrenmek için önceki hizmet yapılandırma örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="c4b56-189">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="c4b56-190">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c4b56-190">Creating the server certificate.</span></span>

     <span data-ttu-id="c4b56-191">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c4b56-191">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="c4b56-192">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="c4b56-192">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c4b56-193">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="c4b56-193">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="c4b56-194">Kurulum toplu iş dosyası, bir hizmet bağımsız değişkeniyle (örneğin,) çalışıyorsa% `setup.bat service` SERVER_NAME% bilgisayarın tam etki alanı adını içerir. Aksi takdirde, varsayılan olarak localhost olur</span><span class="sxs-lookup"><span data-stu-id="c4b56-194">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="c4b56-195">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="c4b56-195">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="c4b56-196">Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c4b56-196">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="c4b56-197">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-197">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c4b56-198">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c4b56-198">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="c4b56-199">U-U olmayan bir. S kullanıyorsanız. Microsoft Windows 'un İngilizce sürümü Setup.bat dosyasını düzenlemeniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-199">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4b56-200">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4b56-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c4b56-201">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c4b56-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c4b56-202">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c4b56-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4b56-203">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4b56-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`
