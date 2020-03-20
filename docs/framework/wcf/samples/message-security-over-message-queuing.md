---
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144441"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="9b2d6-102">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9b2d6-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="9b2d6-103">Bu örnek, istemci için X.509v3 sertifika kimlik doğrulaması ile WS-Security kullanan bir uygulamanın nasıl uygulanacağını ve sunucunun MSMQ üzerinden X.509v3 sertifikasını kullanarak sunucu kimlik doğrulamasını nasıl gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="9b2d6-104">İleti güvenliği, MSMQ deposundaki iletilerin şifrelenmiş kalmasını ve uygulamanın iletinin kendi kimlik doğrulamasını gerçekleştirebilmesini sağlamak için bazen daha fazla tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="9b2d6-105">Bu [örnek, Transacted MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="9b2d6-106">İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b2d6-107">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9b2d6-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9b2d6-108">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9b2d6-109">Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="9b2d6-110">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="9b2d6-111">Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="9b2d6-112">Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="9b2d6-113">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="9b2d6-114">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="9b2d6-115">Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="9b2d6-116">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="9b2d6-117">Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="9b2d6-118">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9b2d6-119">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9b2d6-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="9b2d6-120">Yolun Makecert.exe ve FindPrivateKey.exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="9b2d6-121">Setup.bat'ı örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="9b2d6-122">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b2d6-123">Örneği tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="9b2d6-124">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="9b2d6-125">\service\bin'den Service.exe'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="9b2d6-126">Client.exe'yi \client\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9b2d6-127">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="9b2d6-128">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9b2d6-129">Örneği bilgisayarlarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9b2d6-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="9b2d6-130">Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını servis bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="9b2d6-131">İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="9b2d6-132">İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9b2d6-133">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="9b2d6-134">Sunucuda, çalıştırın. `setup.bat service`</span><span class="sxs-lookup"><span data-stu-id="9b2d6-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="9b2d6-135">Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="9b2d6-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="9b2d6-136">Bilgisayarın tam nitelikli alan adı ile aynı olan yeni sertifika adını `findValue` [ \<(hizmetSertifikası>'ndeki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde hizmetin service.exe.config'ini edin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="9b2d6-137">Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="9b2d6-138">İstemci üzerinde, çalıştırın. `setup.bat client`</span><span class="sxs-lookup"><span data-stu-id="9b2d6-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="9b2d6-139">Bağımsız değişkenle birlikte çalışmak, `setup.bat` client.com adında bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarın. `client`</span><span class="sxs-lookup"><span data-stu-id="9b2d6-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="9b2d6-140">İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="9b2d6-141">Bunu, localhost'u sunucunun tam nitelikli etki alanı adı ile değiştirerek yapın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="9b2d6-142">Ayrıca, hizmet bilgisayarının tam nitelikli alan adı ile aynı olacak şekilde hizmetin sertifika `findValue` adını değiştirmeniz `serviceCertificate` gerekir `clientCredentials`(alt `defaultCertificate` öğedeki öznitelikte).</span><span class="sxs-lookup"><span data-stu-id="9b2d6-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="9b2d6-143">Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="9b2d6-144">İstemci üzerinde, çalıştırın. `ImportServiceCert.bat`</span><span class="sxs-lookup"><span data-stu-id="9b2d6-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="9b2d6-145">Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="9b2d6-146">Sunucuda, çalıştır `ImportClientCert.bat`, Bu LocalMachine istemci.cer dosyasından istemci sertifikası ilerler - Trusted People deposu.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="9b2d6-147">Servis bilgisayarında Service.exe komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="9b2d6-148">İstemci bilgisayarında, komut isteminden Client.exe'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="9b2d6-149">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9b2d6-150">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="9b2d6-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="9b2d6-151">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9b2d6-152">Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9b2d6-153">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9b2d6-154">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b2d6-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b2d6-155">Requirements</span></span>
 <span data-ttu-id="9b2d6-156">Bu örnek, MSMQ'nun yüklü ve çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9b2d6-157">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="9b2d6-157">Demonstrates</span></span>
 <span data-ttu-id="9b2d6-158">İstemci, hizmetin ortak anahtarını kullanarak iletiyi şifreler ve iletiyi kendi sertifikasını kullanarak imzalar.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="9b2d6-159">Kuyruktaki iletiyi okuyan hizmet, istemci sertifikasını güvenilir kişiler deposunda sertifikayla doğrular.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="9b2d6-160">Daha sonra iletinin şifresini çözer ve iletiyi hizmet işlemine gönderir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="9b2d6-161">Windows Communication Foundation (WCF) iletisi MSMQ iletisinin gövdesinde bir yük olarak taşındığından, gövde MSMQ deposunda şifrelenmiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="9b2d6-162">Bu, iletinin istenmeyen şekilde açıklanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="9b2d6-163">MSMQ'nun taşıdığı iletinin şifrelenip şifrelenmediğinin farkında olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="9b2d6-164">Örnek, ileti düzeyinde karşılıklı kimlik doğrulamanın MSMQ ile nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="9b2d6-165">Sertifikalar bant dışı değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="9b2d6-166">Hizmet ve istemci aynı anda çalışır durumda olması gerekmez, çünkü bu her zaman sıralı uygulama ile durumdur.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="9b2d6-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b2d6-167">Description</span></span>
 <span data-ttu-id="9b2d6-168">Örnek istemci ve hizmet kodu, tek bir farkla [İşlenmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="9b2d6-169">İşlem sözleşmesi koruma düzeyiyle ekolarak eklenmiştir ve bu da iletinin imzalanması ve şifrelemesi gerektiğini önerir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="9b2d6-170">İletinin hizmeti ve istemciyi tanımlamak için gerekli belirteç kullanılarak güvenli olduğundan emin olmak için App.config kimlik bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="9b2d6-171">İstemci yapılandırması, hizmetin kimliğini doğrulamak için hizmet sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="9b2d6-172">Hizmetin geçerliliğine güvenmek için LocalMachine mağazasını güvenilir mağaza olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="9b2d6-173">Ayrıca, istemcinin hizmet kimlik doğrulaması için iletiile birlikte eklenen istemci sertifikasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="9b2d6-174">Güvenlik modunun İleti olarak ayarladığını ve ClientCredentialType'ın Sertifika olarak ayarladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="9b2d6-175">Hizmet yapılandırması, istemci hizmeti doğrularken kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışı içerir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="9b2d6-176">Sunucu sertifikası özne adı `findValue` [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)öznitelik belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="9b2d6-177">Örnek, yapılandırmayı kullanarak kimlik doğrulamayı denetlemeyi ve aşağıdaki örnek kodda gösterildiği gibi, arayanın kimliğinin güvenlik bağlamından nasıl alınabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="9b2d6-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="9b2d6-178">Çalıştırıldığında, servis kodu istemci kimliğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="9b2d6-179">Hizmet kodundan örnek çıktı aşağıda veda edilir:</span><span class="sxs-lookup"><span data-stu-id="9b2d6-179">The following is a sample output from the service code:</span></span>

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

## <a name="comments"></a><span data-ttu-id="9b2d6-180">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="9b2d6-180">Comments</span></span>

- <span data-ttu-id="9b2d6-181">İstemci sertifikasıoluşturma.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-181">Creating the client certificate.</span></span>

     <span data-ttu-id="9b2d6-182">Toplu iş dosyasındaki aşağıdaki satır istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="9b2d6-183">Belirtilen istemci adı oluşturulan sertifikanın özne adında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="9b2d6-184">Sertifika mağaza da `My` `CurrentUser` depolanır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="9b2d6-185">İstemci sertifikasını sunucunun güvenilir sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="9b2d6-186">Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını sunucunun Güvenilir Kişiler deposuna kopyalar, böylece sunucu ilgili güven veya güven siz kararları verebilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="9b2d6-187">Trusted People deposunda yüklü bir sertifikanın Bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilen `PeerOrChainTrust` bir `PeerTrust` sertifika için istemci sertifikası doğrulama modunun ayarlanması veya değeri nin ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="9b2d6-188">Bunun bir yapılandırma dosyası kullanarak nasıl yapılabileceğini öğrenmek için önceki hizmet yapılandırma örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="9b2d6-189">Sunucu sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-189">Creating the server certificate.</span></span>

     <span data-ttu-id="9b2d6-190">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="9b2d6-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="9b2d6-191">%SERVER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9b2d6-192">Sertifika LocalMachine mağazasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="9b2d6-193">Kurulum toplu dosyası bir hizmet bağımsız değişkeni (örneğin) `setup.bat service`ile çalıştırılırsa %SERVER_NAME%bilgisayarın tam nitelikli etki alanı adını içerir. Aksi takdirde varsayılan olarak localhost</span><span class="sxs-lookup"><span data-stu-id="9b2d6-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="9b2d6-194">Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="9b2d6-195">Aşağıdaki satır, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9b2d6-196">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9b2d6-197">İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="9b2d6-198">Microsoft Windows'un ABD İngilizce olmayan bir sürümünü kullanıyorsanız, Setup.bat dosyasını düzenlemelisiniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerinizle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b2d6-199">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9b2d6-200">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-200">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9b2d6-201">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b2d6-202">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b2d6-202">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
