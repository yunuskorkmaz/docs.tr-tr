---
title: "İleti Kuyruğa Alma ile İleti Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a63c89e969f7a245dcf14d87872b8d629f1ee846
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="22325-102">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="22325-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="22325-103">Bu örnek, WS-güvenlik X.509v3 sertifika kimlik doğrulaması için istemci ile kullanan ve üzerinde MSMQ sunucunun X.509v3 sertifikasını kullanarak kimlik doğrulaması gerektiren bir uygulama uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22325-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="22325-104">Güvenlik bazen MSMQ depodaki ileti şifreli kalmasını sağlamak için daha fazla tercih ve uygulama ileti iletinin kendi kimlik doğrulaması gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="22325-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>  
  
 <span data-ttu-id="22325-105">Bu örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="22325-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="22325-106">İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="22325-106">The messages are encrypted and signed.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22325-107">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="22325-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="22325-108">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22325-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="22325-109">Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="22325-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="22325-110">Hizmet sırası mevcut değilse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22325-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="22325-111">İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22325-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="22325-112">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="22325-112">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="22325-113">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22325-113">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="22325-114">Genişletme **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="22325-114">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="22325-115">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="22325-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="22325-116">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="22325-116">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="22325-117">Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.</span><span class="sxs-lookup"><span data-stu-id="22325-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="22325-118">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22325-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="22325-119">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="22325-119">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="22325-120">Yolun Makecert.exe ve FindPrivateKey.exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="22325-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>  
  
2.  <span data-ttu-id="22325-121">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="22325-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="22325-122">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="22325-122">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22325-123">Örnekle tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="22325-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="22325-124">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="22325-124">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="22325-125">Service.exe \service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="22325-125">Launch Service.exe from \service\bin.</span></span>  
  
4.  <span data-ttu-id="22325-126">Launch Client.exe from \client\bin.</span><span class="sxs-lookup"><span data-stu-id="22325-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="22325-127">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="22325-127">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="22325-128">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="22325-128">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="22325-129">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="22325-129">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="22325-130">Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="22325-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2.  <span data-ttu-id="22325-131">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="22325-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3.  <span data-ttu-id="22325-132">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="22325-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="22325-133">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="22325-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4.  <span data-ttu-id="22325-134">Sunucu üzerinde çalışan `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="22325-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="22325-135">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="22325-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5.  <span data-ttu-id="22325-136">Yeni sertifika yansıtacak şekilde hizmetin service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="22325-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6.  <span data-ttu-id="22325-137">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="22325-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="22325-138">İstemci üzerinde çalışan `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="22325-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="22325-139">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="22325-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8.  <span data-ttu-id="22325-140">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="22325-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="22325-141">Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="22325-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="22325-142">Hizmeti bilgisayarın tam etki alanı adı ile aynı olması için hizmet sertifikası adını değiştirmeniz gerekir (içinde `findValue` özniteliğini `defaultCertificate` öğesinin `serviceCertificate` altında `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="22325-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="22325-143">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="22325-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="22325-144">İstemci üzerinde çalışan `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="22325-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="22325-145">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="22325-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="22325-146">Sunucu üzerinde çalışan `ImportClientCert.bat`, bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="22325-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="22325-147">Hizmet bilgisayarda komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="22325-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="22325-148">İstemci bilgisayarda komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="22325-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="22325-149">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="22325-149">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="22325-150">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="22325-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="22325-151">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="22325-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22325-152">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="22325-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="22325-153">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="22325-153">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="22325-154">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="22325-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22325-155">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22325-155">Requirements</span></span>  
 <span data-ttu-id="22325-156">Bu örnek, MSMQ yüklü ve çalışıyor olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="22325-156">This sample requires that MSMQ is installed and running.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="22325-157">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="22325-157">Demonstrates</span></span>  
 <span data-ttu-id="22325-158">İstemci hizmeti ortak anahtarını kullanarak ileti şifreler ve kendi sertifikasını kullanarak iletiyi imzalar.</span><span class="sxs-lookup"><span data-stu-id="22325-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="22325-159">Sıradan iletiyi okuma hizmet kendi güvenilir kişiler deposundaki sertifikayı istemci sertifikasıyla kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="22325-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="22325-160">İletinin şifresini çözer ve hizmet işlemi iletiyi gönderir.</span><span class="sxs-lookup"><span data-stu-id="22325-160">It then decrypts the message and dispatches the message to the service operation.</span></span>  
  
 <span data-ttu-id="22325-161">Çünkü [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti yükü MSMQ İleti gövdesi olarak yazımının, gövde MSMQ deposunda şifreli olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="22325-161">Because the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="22325-162">Bu iletinin istenmeyen açığa iletiden güvenliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="22325-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="22325-163">MSMQ kendisini onu taşıyan iletisi olup olmadığını şifrelenir farkında olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22325-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>  
  
 <span data-ttu-id="22325-164">Örnek nasıl karşılıklı kimlik doğrulaması gösterir ileti düzeyi MSMQ ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22325-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="22325-165">Alışverişi-bant sertifikalardır.</span><span class="sxs-lookup"><span data-stu-id="22325-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="22325-166">Hizmet ve istemci aynı anda açık ve çalışıyor olması gerekmez çünkü bu her zaman sıraya alınan uygulamayla durumdur.</span><span class="sxs-lookup"><span data-stu-id="22325-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22325-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22325-167">Description</span></span>  
 <span data-ttu-id="22325-168">Örnek istemci ve hizmet kodu aynı olan [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) bir farkla örnek.</span><span class="sxs-lookup"><span data-stu-id="22325-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="22325-169">İşlem sözleşmesi ileti İmzalanabilir ve şifrelenebilir gerekir, öneren koruma düzeyiyle işaretiyle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="22325-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="22325-170">İstemci ve hizmet tanımlamak için gerekli belirteci kullanarak ileti güvenli olduğundan emin olmak için App.config kimlik bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="22325-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>  
  
 <span data-ttu-id="22325-171">İstemci yapılandırmasında hizmetin kimliğini doğrulamak için hizmet sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="22325-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="22325-172">LocalMachine depolama, hizmet geçerliliğini yararlanmayı güvenilir deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="22325-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="22325-173">Ayrıca istemci hizmeti kimlik doğrulama ileti ile bağlı istemci sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="22325-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>  
  
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
  
 <span data-ttu-id="22325-174">İletiye güvenlik modunu ayarlama ve ClientCredentialType sertifikaya ayarlanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22325-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>  
  
 <span data-ttu-id="22325-175">Hizmet Yapılandırma hizmeti istemci kimlik doğrulaması gerçekleştirdiğinde kullanılan hizmetin kimlik bilgilerini belirtir hizmet davranışı içerir.</span><span class="sxs-lookup"><span data-stu-id="22325-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="22325-176">Sunucu sertifikası konu adı belirtilen `findValue` özniteliğini [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="22325-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="22325-177">Örnek Yapılandırması ve güvenlik bağlamından çağıranının kimliğini edinme aşağıdaki örnek kodda gösterildiği gibi kullanarak denetleme kimlik doğrulaması gösterir:</span><span class="sxs-lookup"><span data-stu-id="22325-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>  
  
```  
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
  
 <span data-ttu-id="22325-178">Çalıştırdığınızda, servis kodunu istemci kimliğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22325-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="22325-179">Hizmet kodundan örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="22325-179">The following is a sample output from the service code:</span></span>  
  
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
  
## <a name="comments"></a><span data-ttu-id="22325-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22325-180">Comments</span></span>  
  
-   <span data-ttu-id="22325-181">İstemci sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="22325-181">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="22325-182">Toplu iş dosyasında aşağıdaki satırı istemci sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22325-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="22325-183">Belirtilen istemci adı oluşturulan sertifika konu adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22325-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="22325-184">Sertifika depolandığı `My` adresindeki depolamak `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="22325-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="22325-185">İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="22325-185">Installing the client certificate into server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="22325-186">Toplu dosya kopyalarını aşağıdaki satırda sunucunun TrustedPeople içine istemci sertifikası sunucu ilgili güven veya no güven kararları yapabilmek depolar.</span><span class="sxs-lookup"><span data-stu-id="22325-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="22325-187">Tarafından güvenilmesi için TrustedPeople deposundaki yüklü bir sertifika için bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti, istemci sertifikası doğrulama modunu ayarlanmalıdır `PeerOrChainTrust` veya `PeerTrust` değeri.</span><span class="sxs-lookup"><span data-stu-id="22325-187">For a certificate installed in the TrustedPeople store to be trusted by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="22325-188">Önceki hizmet yapılandırma örneği bu nasıl yapılabilir bilgi edinmek için bkz: bir yapılandırma dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="22325-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="22325-189">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="22325-189">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="22325-190">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="22325-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="22325-191">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22325-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="22325-192">Sertifika saklanır LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="22325-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="22325-193">Kurulum toplu iş dosyası hizmetinin bağımsız değişkenlerle çalıştırırsanız (gibi `setup.bat service`) sunucu_adı % bilgisayarın tam etki alanı adını içerir. Aksi takdirde localhost için varsayılan olarak</span><span class="sxs-lookup"><span data-stu-id="22325-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>  
  
-   <span data-ttu-id="22325-194">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="22325-194">Installing server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="22325-195">Aşağıdaki satırı sunucu sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="22325-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="22325-196">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="22325-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="22325-197">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="22325-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="22325-198">ABD dışındaki kullanıyorsanız Setup.bat düzenlemelisiniz Windows dosya ve "NT AUTHORITY\NETWORK SERVICE" hesap adı, bölgesel eşdeğerleriyle değiştirme Microsoft İngilizce sürümü.</span><span class="sxs-lookup"><span data-stu-id="22325-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22325-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="22325-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="22325-200">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="22325-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="22325-201">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="22325-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22325-202">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="22325-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="22325-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22325-203">See Also</span></span>
