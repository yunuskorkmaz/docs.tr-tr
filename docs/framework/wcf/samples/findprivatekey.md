---
title: FindPrivateKey örneği - WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490776"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="8579d-102">FindPrivateKey örnek</span><span class="sxs-lookup"><span data-stu-id="8579d-102">FindPrivateKey sample</span></span>

<span data-ttu-id="8579d-103">Sertifika deposundaki belirli bir X.509 sertifikasıyla ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8579d-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="8579d-104">FindPrivateKey.exe aracı bu işlemi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8579d-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8579d-105">FindPrivateKey kullanmadan önce derlenmiş olması gereken bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="8579d-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="8579d-106">Bkz: [FindPrivateKey Projeyi derlemek için](#to-build-the-findprivatekey-project) bölüm derleme FindPrivateKey aracı hakkında yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="8579d-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="8579d-107">X.509 sertifikalarına bir yönetici veya makinede bulunan herhangi bir kullanıcı tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8579d-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="8579d-108">Ancak, sertifika, farklı bir hesap altında çalışan bir hizmet tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8579d-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="8579d-109">Örneğin, ağ hizmeti hesabı.</span><span class="sxs-lookup"><span data-stu-id="8579d-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="8579d-110">Bu hesap sertifikası tarafından başlangıçta yüklenmediğinden özel anahtar dosyasına erişimi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8579d-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="8579d-111">FindPrivateKey Aracı'nı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="8579d-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="8579d-112">İzinleri eklemek veya belirli X.509 sertifikalarının özel anahtar dosyasının konumunu bilmek sonra bu dosyaya izinleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8579d-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="8579d-113">Güvenlik için sertifikaları kullanma örnekleri FindPrivateKey aracını *Setup.bat* dosya.</span><span class="sxs-lookup"><span data-stu-id="8579d-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="8579d-114">Özel anahtar dosyası bulunamadı sonra gibi diğer araçları kullanın *Cacls.exe* dosyasını uygun erişim haklarını ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="8579d-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="8579d-115">Bir Windows Communication Foundation (WCF) hizmet şirket içinde barındırılan bir yürütülebilir dosya gibi bir kullanıcı hesabı altında çalışıyorsa, kullanıcı hesabının dosyaya salt okunur erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8579d-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="8579d-116">Bir WCF hizmeti Internet Information Services (IIS) altında çalışırken hizmetin altında çalıştığı varsayılan IIS 7 ve önceki sürümlerde ağ hizmeti veya IIS 7.5 ve üzeri sürümler üzerinde uygulama havuzu kimliği hesaplarıdır.</span><span class="sxs-lookup"><span data-stu-id="8579d-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="8579d-117">Daha fazla bilgi için [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="8579d-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="8579d-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8579d-118">Examples</span></span>

<span data-ttu-id="8579d-119">İşlemi okuma ayrıcalığına sahip değil bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="8579d-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="8579d-120">Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından sağ hizmetinin altında çalışmakta olduğu işlem için erişim ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8579d-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="8579d-121">Örneğin, bu için Cacls.exe aracının aşağıdaki örnekte gösterildiği gibi yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="8579d-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="8579d-122">FindPrivateKey projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8579d-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="8579d-123">Projeyi indirmek için şurayı ziyaret edin [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="8579d-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="8579d-124">Dosya Gezgini'ni açın ve gidin *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* klasörü altında örnek yüklediğiniz dizin konumu.</span><span class="sxs-lookup"><span data-stu-id="8579d-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="8579d-125">Visual Studio'da dosyayı açmak için bir .sln dosya simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8579d-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="8579d-126">İçinde **derleme** menüsünde **çözümü yeniden derle**.</span><span class="sxs-lookup"><span data-stu-id="8579d-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="8579d-127">Çözümü derledikten dosyası oluşturur: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="8579d-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="8579d-128">Kuralları — komut satırı girişleri</span><span class="sxs-lookup"><span data-stu-id="8579d-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="8579d-129">"[*seçeneği*]" isteğe bağlı parametrelerinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8579d-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="8579d-130">"{*seçeneği*}" zorunlu bir parametre kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8579d-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="8579d-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span><span class="sxs-lookup"><span data-stu-id="8579d-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="8579d-132">"\<*değer*>" girilmesi bir parametre değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8579d-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="8579d-133">Kullanım</span><span class="sxs-lookup"><span data-stu-id="8579d-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="8579d-134">Konum:</span><span class="sxs-lookup"><span data-stu-id="8579d-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="8579d-135">Komut isteminde parametre belirtilirse, ardından bu Yardım metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8579d-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="8579d-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8579d-136">Examples</span></span>

<span data-ttu-id="8579d-137">Bu örnek dosya adının sertifikanın konu adını bulur "CN = localhost", geçerli kullanıcının kişisel depoda.</span><span class="sxs-lookup"><span data-stu-id="8579d-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="8579d-138">Bu örnek dosya adının sertifikanın konu adını bulur "CN = localhost", kişisel geçerli kullanıcının depolamak ve çıkış tam dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="8579d-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="8579d-139">Bu örnekte adla sertifikanın parmak izini bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposuna.</span><span class="sxs-lookup"><span data-stu-id="8579d-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
