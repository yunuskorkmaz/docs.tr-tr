---
title: "FindPrivateKey örnek - WCF"
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32e1a4a3de01371d67be8d19613b1f29c1ce3c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="7834e-102">FindPrivateKey örnek</span><span class="sxs-lookup"><span data-stu-id="7834e-102">FindPrivateKey sample</span></span>

<span data-ttu-id="7834e-103">Belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7834e-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="7834e-104">FindPrivateKey.exe aracı bu işlemi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7834e-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7834e-105">FindPrivateKey kullanmak için derlenmiş önceki olması gereken bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="7834e-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="7834e-106">Bkz: [FindPrivateKey Projeyi derlemek için](#to-build-the-findprivatekey-project) bölüm FindPrivateKey aracını yapılandırma hakkında yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="7834e-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="7834e-107">X.509 sertifikaları, bir yönetici veya makinede herhangi bir kullanıcı tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7834e-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="7834e-108">Ancak, sertifika başka bir hesap altında çalışan bir hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7834e-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="7834e-109">Örneğin, ağ hizmeti hesabı.</span><span class="sxs-lookup"><span data-stu-id="7834e-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="7834e-110">Sertifika tarafından başlangıçta yüklenmediğinden bu hesap için özel anahtar dosyası erişimi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7834e-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="7834e-111">FindPrivateKey aracı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="7834e-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="7834e-112">İzinleri eklemek veya bu dosyaya izinleri belirli X.509 sertifikalarının özel anahtar dosyasının konumunu öğrendikten sonra kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7834e-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="7834e-113">Güvenlik için sertifikaları kullanma örnekleri FindPrivateKey aracını *Setup.bat* dosya.</span><span class="sxs-lookup"><span data-stu-id="7834e-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="7834e-114">Özel anahtar dosyası bulunamadı sonra gibi diğer araçları kullanarak *Cacls.exe* dosyanın uygun erişim haklarına ayarlanamadı.</span><span class="sxs-lookup"><span data-stu-id="7834e-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="7834e-115">Windows Communication Foundation (WCF) hizmetini kendini barındıran bir yürütülebilir dosya gibi bir kullanıcı hesabı altında çalışan kullanıcı hesabı dosyaya salt okunur erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7834e-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="7834e-116">Bir WCF hizmeti Internet Information Services (IIS) altında çalışırken, altında çalışacağı varsayılan IIS 7 ve önceki sürümlerde ağ hizmet veya uygulama havuzu kimliği IIS 7.5 ve sonraki sürümlerde hesaplarıdır.</span><span class="sxs-lookup"><span data-stu-id="7834e-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="7834e-117">Daha fazla bilgi için bkz: [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="7834e-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="7834e-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7834e-118">Examples</span></span>

<span data-ttu-id="7834e-119">İşlem okuma ayrıcalığına sahip olmayan bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi bakın:</span><span class="sxs-lookup"><span data-stu-id="7834e-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="7834e-120">Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından erişim hakkı hizmetinin altında çalışan işlemi için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7834e-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="7834e-121">Örneğin, bu Cacls.exe aracıyla aşağıdaki örnekte gösterildiği gibi yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="7834e-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="7834e-122">FindPrivateKey projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7834e-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="7834e-123">Proje indirmek için şurayı ziyaret edin [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="7834e-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="7834e-124">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] gidin *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* örnek yüklendiği dizin konumu altında bir klasör.</span><span class="sxs-lookup"><span data-stu-id="7834e-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="7834e-125">Visual Studio'da dosyayı açmaya .sln dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7834e-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="7834e-126">İçinde **yapı** menüsünde, select **çözümü yeniden derle**.</span><span class="sxs-lookup"><span data-stu-id="7834e-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="7834e-127">Çözümü derleme dosyası oluşturur: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="7834e-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="7834e-128">Kuralları — komut satırı girişleri</span><span class="sxs-lookup"><span data-stu-id="7834e-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="7834e-129">"[*seçeneği*]" bir isteğe bağlı parametreleri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7834e-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="7834e-130">"{*seçeneği*}" parametreleri zorunlu kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7834e-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="7834e-131">"*seçenek 1* &#124; *Seçenek2*"seçenekleri kümesi arasında bir seçim temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7834e-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="7834e-132">"\<*değeri*>" girilecek bir parametre değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7834e-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="7834e-133">Kullanım</span><span class="sxs-lookup"><span data-stu-id="7834e-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="7834e-134">Konum:</span><span class="sxs-lookup"><span data-stu-id="7834e-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="7834e-135">Hiçbir parametre komut isteminde belirtilirse, bu Yardım metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7834e-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="7834e-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7834e-136">Examples</span></span>

<span data-ttu-id="7834e-137">Bu örnek sertifika filename konu adıyla bulur "CN = localhost", geçerli kullanıcının kişisel deposunda.</span><span class="sxs-lookup"><span data-stu-id="7834e-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="7834e-138">Bu örnek sertifika filename konu adıyla bulur "CN = localhost", Kişisel depolama geçerli kullanıcının ve çıkış tam dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="7834e-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="7834e-139">Bu örnek dosya adının sertifikanın parmak izi bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposunda.</span><span class="sxs-lookup"><span data-stu-id="7834e-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
