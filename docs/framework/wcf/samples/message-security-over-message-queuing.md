---
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: ec79309b9959faa131ee13ff589a10ee1054f27d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835888"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="75dfc-102">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="75dfc-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="75dfc-103">Bu örnek X.509v3 sertifika kimlik doğrulaması için istemci ile WS-güvenlik kullanan ve üzerinde MSMQ sunucusunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="75dfc-104">Güvenlik bazen MSMQ depodaki ileti şifrelenmiş kalmasını sağlamak için daha fazla tercih ve uygulama ileti iletinin kendi kimlik doğrulaması gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75dfc-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="75dfc-105">Bu örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="75dfc-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="75dfc-106">İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="75dfc-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="75dfc-107">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="75dfc-107">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="75dfc-108">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75dfc-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="75dfc-109">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="75dfc-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="75dfc-110">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="75dfc-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="75dfc-111">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75dfc-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="75dfc-112">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="75dfc-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="75dfc-113">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-113">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="75dfc-114">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="75dfc-114">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="75dfc-115">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="75dfc-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="75dfc-116">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="75dfc-116">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="75dfc-117">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="75dfc-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="75dfc-118">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75dfc-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="75dfc-119">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="75dfc-119">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="75dfc-120">Makecert.exe ve FindPrivateKey.exe içeren klasörün yolunu içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="75dfc-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2.  <span data-ttu-id="75dfc-121">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="75dfc-122">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="75dfc-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="75dfc-123">Örnek ile tamamladığınızda Cleanup.bat çalıştırarak, sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="75dfc-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="75dfc-124">Diğer güvenlik örnekleri aynı sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-124">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="75dfc-125">Service.exe \service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-125">Launch Service.exe from \service\bin.</span></span>  
  
4.  <span data-ttu-id="75dfc-126">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="75dfc-127">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-127">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="75dfc-128">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75dfc-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="75dfc-129">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="75dfc-129">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="75dfc-130">Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2.  <span data-ttu-id="75dfc-131">İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="75dfc-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3.  <span data-ttu-id="75dfc-132">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="75dfc-133">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4.  <span data-ttu-id="75dfc-134">Sunucu üzerinde çalışan `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="75dfc-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="75dfc-135">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5.  <span data-ttu-id="75dfc-136">Yeni sertifika adını yansıtacak şekilde hizmetin service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="75dfc-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6.  <span data-ttu-id="75dfc-137">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="75dfc-138">Bir istemcide çalışmasına `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="75dfc-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="75dfc-139">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8.  <span data-ttu-id="75dfc-140">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="75dfc-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="75dfc-141">Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="75dfc-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="75dfc-142">Sertifika adı hizmetin hizmet bilgisayarın tam etki alanı adı ile aynı olması da değiştirmeniz gerekir (içinde `findValue` özniteliğini `defaultCertificate` öğesinin `serviceCertificate` altında `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="75dfc-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="75dfc-143">Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="75dfc-144">Bir istemcide çalışmasına `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="75dfc-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="75dfc-145">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="75dfc-146">Sunucu üzerinde çalışan `ImportClientCert.bat`, bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="75dfc-147">Hizmet bilgisayarda Service.exe Komut İstemi'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="75dfc-148">İstemci bilgisayarda komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="75dfc-149">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75dfc-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="75dfc-150">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="75dfc-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="75dfc-151">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75dfc-152">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="75dfc-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="75dfc-153">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="75dfc-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="75dfc-154">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="75dfc-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="75dfc-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75dfc-155">Requirements</span></span>
 <span data-ttu-id="75dfc-156">Bu örnek, MSMQ yüklü ve çalışıyor olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="75dfc-157">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="75dfc-157">Demonstrates</span></span>
 <span data-ttu-id="75dfc-158">İstemci, hizmeti ortak anahtarını kullanarak ileti şifreler ve iletiyi kendi sertifikasını kullanarak imzalar.</span><span class="sxs-lookup"><span data-stu-id="75dfc-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="75dfc-159">Kuyruktan ileti okuma hizmeti, güvenilir kişiler deposunda sertifika ile istemci sertifikası kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="75dfc-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="75dfc-160">İletinin şifresini çözer ve hizmet işlemi iletiyi gönderir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="75dfc-161">Windows Communication Foundation (WCF) ileti bir MSMQ iletisinin gövdesi, yükteki olarak yürütülür çünkü gövdesi MSMQ deposunda şifreli olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="75dfc-162">Bu, istenmeyen ileti açıklanması ileti güvenliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="75dfc-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="75dfc-163">MSMQ kendisi, yürütme iletisi olup olmadığını şifrelenir farkında olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="75dfc-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="75dfc-164">Nasıl karşılıklı kimlik doğrulaması örneği gösterir ileti düzeyi MSMQ ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="75dfc-165">Sertifika alışverişi olur-bant var.</span><span class="sxs-lookup"><span data-stu-id="75dfc-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="75dfc-166">Hizmet ve istemci aynı anda açık ve çalışıyor olması gerekmez çünkü bu her zaman kuyruğa alınan uygulamayı durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="75dfc-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75dfc-167">Description</span></span>
 <span data-ttu-id="75dfc-168">Örnek hizmet ve istemci kodu aynı olan [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek bir fark dışında.</span><span class="sxs-lookup"><span data-stu-id="75dfc-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="75dfc-169">İşlem anlaşması iletinin imzalanmış ve şifrelenmiş gerekir, önerir koruma düzeyi ile açıklanıyor.</span><span class="sxs-lookup"><span data-stu-id="75dfc-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="75dfc-170">Hizmet ve istemci tanımlamak için gerekli belirteci kullanarak ileti güvenli olduğundan emin olmak için App.config kimlik bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="75dfc-171">İstemci yapılandırmasında hizmetin kimliğini doğrulamak için hizmet sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="75dfc-172">Kendi LocalMachine deposu, hizmetin üzerinde geçerlilik yararlanmayı güvenilen deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="75dfc-173">Ayrıca İstemcinin hizmete kimlik doğrulaması için bir ileti ile bağlı istemci sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="75dfc-174">İleti ve ClientCredentialType güvenlik modunu ayarlama Not sertifika için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="75dfc-175">Hizmet yapılandırmasının hizmet istemcisi kimlik doğrulamasını gerçekleştirdiğinde kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışını içerir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="75dfc-176">Sunucu sertifikası konu adı belirtilen `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="75dfc-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="75dfc-177">Örnek denetleme kimlik doğrulaması yapılandırması ve güvenlik bağlamından çağıranının kimliğini edinme aşağıdaki örnek kodda gösterildiği gibi kullanarak göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="75dfc-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="75dfc-178">Çalıştırdığınızda, istemci kimliği hizmet kodunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="75dfc-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="75dfc-179">Hizmet kodu örnek çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75dfc-179">The following is a sample output from the service code:</span></span>

```
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

## <a name="comments"></a><span data-ttu-id="75dfc-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75dfc-180">Comments</span></span>

-   <span data-ttu-id="75dfc-181">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="75dfc-181">Creating the client certificate.</span></span>

     <span data-ttu-id="75dfc-182">Toplu iş dosyasında aşağıdaki satırı, istemci sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75dfc-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="75dfc-183">Belirtilen istemci adı, oluşturulan sertifikanın konu adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75dfc-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="75dfc-184">Sertifika depolandığı `My` konumunda depolamak `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="75dfc-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="75dfc-185">İstemci sertifikası sunucusunun güvenilen sertifika depolama alanına yükleme.</span><span class="sxs-lookup"><span data-stu-id="75dfc-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="75dfc-186">Toplu dosya kopyalarını aşağıdaki satırda sunucunun TrustedPeople istemci sertifikayı sunucu ilgili güveni veya no güven kararları yapabilmeleri için depolar.</span><span class="sxs-lookup"><span data-stu-id="75dfc-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="75dfc-187">Bir Windows Communication Foundation (WCF) hizmeti tarafından güvenilmesi için TrustedPeople deposunda yüklü bir sertifika için istemci sertifika doğrulama modunu ayarlamak `PeerOrChainTrust` veya `PeerTrust` değeri.</span><span class="sxs-lookup"><span data-stu-id="75dfc-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="75dfc-188">Önceki hizmet yapılandırma örneği bu nasıl yapılabilir bilgi edinmek için bkz. yapılandırma dosyası kullanma.</span><span class="sxs-lookup"><span data-stu-id="75dfc-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="75dfc-189">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="75dfc-189">Creating the server certificate.</span></span>

     <span data-ttu-id="75dfc-190">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="75dfc-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="75dfc-191">% Sunucu_adı % değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="75dfc-192">Depolanmış bir sertifikayla LocalMachine depolama.</span><span class="sxs-lookup"><span data-stu-id="75dfc-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="75dfc-193">Kurulum toplu iş dosyasını hizmet bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir. Aksi takdirde localhost için varsayılan olarak</span><span class="sxs-lookup"><span data-stu-id="75dfc-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

-   <span data-ttu-id="75dfc-194">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="75dfc-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="75dfc-195">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="75dfc-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="75dfc-196">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="75dfc-197">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="75dfc-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="75dfc-198">ABD dışı kullanıyorsanız İngilizce sürümü Microsoft Setup.bat düzenlemelisiniz Windows dosya ve "NT AUTHORITY\NETWORK SERVICE" hesap adı, bölgesel eşdeğerleriyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="75dfc-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="75dfc-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="75dfc-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="75dfc-200">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="75dfc-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75dfc-201">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="75dfc-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75dfc-202">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="75dfc-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
