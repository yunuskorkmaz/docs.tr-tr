---
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: ce4cd76a053b9b3611751fe081d0ca710240049d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555711"
---
# <a name="custom-binding-security"></a><span data-ttu-id="df2ff-102">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="df2ff-102">Custom Binding Security</span></span>

<span data-ttu-id="df2ff-103">Bu örnek, bir özel bağlama kullanılarak güvenliğin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="df2ff-104">Güvenli bir aktarımla ileti düzeyi güvenliği etkinleştirmek için özel bağlamayı nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="df2ff-105">Bu, iletileri istemci ve hizmet arasında iletmek için güvenli bir aktarım gerektiğinde ve iletilerin ileti düzeyinde güvenli olması gerektiği durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="df2ff-106">Bu yapılandırma sistem tarafından belirtilen bağlamalar tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="df2ff-106">This configuration is not supported by system-provided bindings.</span></span>

<span data-ttu-id="df2ff-107">Bu örnek, bir istemci konsol programından (EXE) ve bir hizmet konsolu programından (EXE) oluşur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="df2ff-108">Hizmet bir çift yönlü sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="df2ff-108">The service implements a duplex contract.</span></span> <span data-ttu-id="df2ff-109">Sözleşme, `ICalculatorDuplex` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="df2ff-110">`ICalculatorDuplex`Arabirim, istemcinin bir oturum üzerinde çalışan bir sonucu hesaplamak için matematik işlemleri gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="df2ff-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="df2ff-111">Bağımsız olarak, hizmet sonuçları `ICalculatorDuplexCallback` arabirime döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="df2ff-112">Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="df2ff-113">Çift yönlü iletişimi destekleyen ve güvenli hale gelen özel bir bağlama tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="df2ff-114">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="df2ff-115">Hizmet yapılandırması aşağıdakileri destekleyen özel bir bağlama tanımlar:</span><span class="sxs-lookup"><span data-stu-id="df2ff-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="df2ff-116">TLS/SSL protokolü kullanılarak korunan TCP iletişimi.</span><span class="sxs-lookup"><span data-stu-id="df2ff-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="df2ff-117">Windows ileti güvenliği.</span><span class="sxs-lookup"><span data-stu-id="df2ff-117">Windows message security.</span></span>

<span data-ttu-id="df2ff-118">Özel bağlama yapılandırması, ileti düzeyi güvenliği aynı anda etkinleştirerek güvenli aktarımı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="df2ff-119">Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="df2ff-120">Özel bağlama, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmette ve istemci yapılandırma dosyalarında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

<span data-ttu-id="df2ff-121">Özel bağlama, Aktarım düzeyinde hizmetin kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="df2ff-122">Bu, `sslStreamSecurity` Binding öğesi tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="df2ff-123">Hizmetin sertifikası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışı kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="df2ff-124">Ayrıca, özel bağlama Windows kimlik bilgisi türü ile ileti güvenliği kullanır-bu, varsayılan kimlik bilgisi türüdür.</span><span class="sxs-lookup"><span data-stu-id="df2ff-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="df2ff-125">Bu, `security` Binding öğesi tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="df2ff-126">Kerberos kimlik doğrulama mekanizması kullanılabiliyorsa, istemci ve hizmetin her ikisi de ileti düzeyi güvenlik kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="df2ff-127">Bu, örnek Active Directory ortamda çalıştırıldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="df2ff-128">Kerberos kimlik doğrulama mekanizması kullanılamıyorsa, NTLM kimlik doğrulaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="df2ff-129">NTLM, istemcinin hizmet kimliğini doğrular, ancak hizmette hizmetin kimliğini doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="df2ff-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="df2ff-130">`security`Bağlama öğesi kullanmak üzere yapılandırılmıştır `SecureConversation` `authenticationType` , bu da hem istemcide hem de hizmette bir güvenlik oturumu oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="df2ff-131">Bu, hizmetin çift yönlü sözleşmesinin çalışmasını sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-131">This is required to enable the service's duplex contract to work.</span></span>

<span data-ttu-id="df2ff-132">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="df2ff-133">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-133">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="df2ff-134">Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye döndürülen iletileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="df2ff-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="df2ff-135">Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="df2ff-136">İstemcisini kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-136">Press ENTER to shut down the client.</span></span>

<span data-ttu-id="df2ff-137">Eklenen Setup.bat dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için istemciyi ve sunucuyu ilgili hizmet sertifikasıyla yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="df2ff-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="df2ff-138">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="df2ff-139">Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, bu örneğe uygulanan toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="df2ff-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="df2ff-140">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="df2ff-140">Creating the server certificate.</span></span>

  <span data-ttu-id="df2ff-141">Setup.bat dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="df2ff-142">`%SERVER_NAME%`Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="df2ff-143">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df2ff-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="df2ff-144">Bu toplu iş dosyası, sunucu adını localhost olarak varsayılan olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="df2ff-144">This batch file defaults the server name to localhost.</span></span>

  <span data-ttu-id="df2ff-145">Sertifika, Web 'de barındırılan hizmetler için CurrentUser deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- <span data-ttu-id="df2ff-146">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="df2ff-146">Installing the server certificate into the client's trusted certificate store.</span></span>

  <span data-ttu-id="df2ff-147">Setup.bat dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="df2ff-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="df2ff-148">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="df2ff-149">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="df2ff-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > <span data-ttu-id="df2ff-150">Setup.bat Batch dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="df2ff-151">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="df2ff-152">Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="df2ff-153">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="df2ff-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="df2ff-154">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="df2ff-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="df2ff-155">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="df2ff-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="df2ff-156">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="df2ff-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="df2ff-157">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="df2ff-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="df2ff-158">Yönetici ayrıcalıklarıyla Visual Studio için bir Geliştirici Komut İstemi açın ve örnek yüklemesi klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="df2ff-159">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="df2ff-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="df2ff-160">Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="df2ff-161">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="df2ff-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="df2ff-162">\Service\bin. 'den başlatma Service.exe</span><span class="sxs-lookup"><span data-stu-id="df2ff-162">Launch Service.exe from \service\bin.</span></span>

3. <span data-ttu-id="df2ff-163">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="df2ff-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="df2ff-164">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="df2ff-165">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="df2ff-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="df2ff-166">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="df2ff-166">To run the sample across computers</span></span>

1. <span data-ttu-id="df2ff-167">Hizmet bilgisayarında:</span><span class="sxs-lookup"><span data-stu-id="df2ff-167">On the service computer:</span></span>

    1. <span data-ttu-id="df2ff-168">Hizmet bilgisayarında servicemodelsamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="df2ff-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>

    2. <span data-ttu-id="df2ff-169">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="df2ff-170">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="df2ff-170">Ensure that you copy the files in the \bin subdirectory.</span></span>

    3. <span data-ttu-id="df2ff-171">Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>

    4. <span data-ttu-id="df2ff-172">Yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi için aşağıdaki komutu çalıştırın: `Setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="df2ff-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="df2ff-173">Bu işlem, toplu iş dosyasının çalıştırıldığı bilgisayarın adıyla eşleşen konu adına sahip hizmet sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df2ff-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>

        > [!NOTE]
        > <span data-ttu-id="df2ff-174">Setup.bat Batch dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="df2ff-175">PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="df2ff-176">Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="df2ff-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="df2ff-177">[\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)Service.exe.config dosyanın içinde, önceki adımda oluşturulan sertifikanın konu adını yansıtacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="df2ff-177">Change the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="df2ff-178">Komut isteminden Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="df2ff-179">İstemci bilgisayarda:</span><span class="sxs-lookup"><span data-stu-id="df2ff-179">On the client computer:</span></span>

    1. <span data-ttu-id="df2ff-180">İstemci program dosyalarını \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="df2ff-181">Cleanup.bat dosyasını da kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="df2ff-182">Önceki örneklerden gelen eski sertifikaları kaldırmak için Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="df2ff-183">Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açarak ve hizmet bilgisayarında aşağıdaki komutu çalıştırarak hizmetin sertifikasını dışarı aktarın ( `%SERVER_NAME%` hizmetin çalıştığı bilgisayarın tam adıyla değiştirin):</span><span class="sxs-lookup"><span data-stu-id="df2ff-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="df2ff-184">% SERVER_NAME%. cer öğesini istemci bilgisayara kopyalayın (% SERVER_NAME% değerini hizmetin çalıştığı bilgisayarın tam adı ile değiştirin).</span><span class="sxs-lookup"><span data-stu-id="df2ff-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="df2ff-185">Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açarak hizmetin sertifikasını içeri aktarın ve istemci bilgisayarda aşağıdaki komutu çalıştırın (% SERVER_NAME% değerini hizmetin çalıştığı bilgisayarın tam adı ile değiştirin):</span><span class="sxs-lookup"><span data-stu-id="df2ff-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        <span data-ttu-id="df2ff-186">Sertifika güvenilen bir veren tarafından verildiyse, c, d ve e adımları gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="df2ff-187">İstemcinin App.config dosyasını aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="df2ff-187">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
                behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="df2ff-188">Hizmet, bir etki alanı ortamında NetworkService veya LocalSystem hesabı dışında bir hesap altında çalışıyorsa, hizmeti çalıştırmak için kullanılan hesaba göre uygun UPN veya SPN 'yi ayarlamak için istemci App.config dosyası içindeki hizmet uç noktası kimliğini değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="df2ff-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="df2ff-189">Uç nokta kimliği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulama](../feature-details/service-identity-and-authentication.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="df2ff-189">For more information about endpoint identity, see the [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="df2ff-190">Komut isteminden Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="df2ff-191">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="df2ff-191">To clean up after the sample</span></span>

- <span data-ttu-id="df2ff-192">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="df2ff-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
