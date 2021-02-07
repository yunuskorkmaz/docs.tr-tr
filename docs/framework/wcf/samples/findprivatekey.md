---
description: 'Hakkında daha fazla bilgi edinin: FindPrivateKey Sample'
title: FindPrivateKey örneği
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 0e876aa3e1f6dde16acbb3ddd2a130ad49d369fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732429"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="61f03-103">FindPrivateKey örneği</span><span class="sxs-lookup"><span data-stu-id="61f03-103">FindPrivateKey sample</span></span>

<span data-ttu-id="61f03-104">Sertifika deposundaki belirli bir X. 509.440 sertifikasıyla ilişkili özel anahtar dosyasının konumunu ve adını bulmak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="61f03-104">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="61f03-105">FindPrivateKey.exe aracı bu işlemi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="61f03-105">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61f03-106">FindPrivateKey, kullanılmadan önce derlenmesi gereken bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="61f03-106">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="61f03-107">FindPrivateKey aracının nasıl oluşturulacağı hakkında yönergeler için bkz. [FindPrivateKey projesi oluşturmak için](#to-build-the-findprivatekey-project) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="61f03-107">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="61f03-108">X. 509.440 sertifikaları bir yönetici veya makinedeki herhangi bir kullanıcı tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="61f03-108">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="61f03-109">Ancak, sertifikaya farklı bir hesap altında çalışan bir hizmet tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="61f03-109">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="61f03-110">Örneğin, ağ HIZMETI hesabı.</span><span class="sxs-lookup"><span data-stu-id="61f03-110">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="61f03-111">Sertifika, ilk olarak yüklenmediği için bu hesabın özel anahtar dosyasına erişimi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="61f03-111">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="61f03-112">FindPrivateKey Aracı, belirli bir X. 509.440 sertifikasının özel anahtar dosyasının konumunu verir.</span><span class="sxs-lookup"><span data-stu-id="61f03-112">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="61f03-113">Belirli bir X. 509.952 sertifikaları ' özel anahtar dosyasının konumunu öğrendikten sonra bu dosyaya izinler ekleyebilir veya izinleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f03-113">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="61f03-114">Güvenlik için sertifikaları kullanan örnekler, *Setup.bat* dosyasında FindPrivateKey aracını kullanır.</span><span class="sxs-lookup"><span data-stu-id="61f03-114">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="61f03-115">Özel anahtar dosyası bulduktan sonra, dosya üzerinde uygun erişim haklarını ayarlamak için *Cacls.exe* gibi diğer araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61f03-115">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="61f03-116">Şirket içinde barındırılan yürütülebilir dosya gibi bir kullanıcı hesabı altında bir Windows Communication Foundation (WCF) hizmeti çalıştırırken, Kullanıcı hesabının dosyaya salt okuma erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="61f03-116">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="61f03-117">Internet Information Services (IIS) altında bir WCF Hizmeti çalıştırırken, hizmetin altında çalıştığı varsayılan hesaplar IIS 7 ve önceki sürümlerde ağ HIZMETI ya da IIS 7,5 ve sonraki sürümlerde uygulama havuzu kimliği ' nde bulunur.</span><span class="sxs-lookup"><span data-stu-id="61f03-117">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="61f03-118">Daha fazla bilgi için bkz. [uygulama havuzu kimlikleri](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="61f03-118">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="61f03-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="61f03-119">Examples</span></span>

<span data-ttu-id="61f03-120">İşlemin okuma ayrıcalıklarına sahip olmadığı bir sertifikaya erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="61f03-120">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="61f03-121">Bu durumda, özel anahtar dosyasını bulmak için FindPrivateKey aracını kullanın ve ardından hizmetin altında çalıştığı işlem için erişim hakkını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="61f03-121">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="61f03-122">Örneğin, bu, aşağıdaki örnekte gösterildiği gibi Cacls.exe aracı ile yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="61f03-122">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="61f03-123">FindPrivateKey projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="61f03-123">To build the FindPrivateKey project</span></span>

<span data-ttu-id="61f03-124">Projeyi indirmek için [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerini](https://www.microsoft.com/download/details.aspx?id=21459)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="61f03-124">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="61f03-125">Dosya Gezgini 'ni açın ve örneği yüklediğiniz dizin konumunda *WF_WCF_Samples \wcf\setup\findprivatekey\cs* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="61f03-125">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="61f03-126">Visual Studio 'da dosyayı açmak için. sln dosya simgesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="61f03-126">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="61f03-127">**Derle** menüsünde **çözümü yeniden derle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="61f03-127">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="61f03-128">Çözümü oluşturmak dosyayı oluşturur: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="61f03-128">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="61f03-129">Kurallar — komut satırı girdileri</span><span class="sxs-lookup"><span data-stu-id="61f03-129">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="61f03-130">"[*seçenek*]", isteğe bağlı bir parametre kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61f03-130">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="61f03-131">"{*Option*}", zorunlu bir parametre kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61f03-131">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="61f03-132">"*seçenek1* &#124; *Seçenek2*" seçenek kümeleri arasında bir seçimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61f03-132">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="61f03-133">" \<*value*> " girilecek bir parametre değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61f03-133">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="61f03-134">Kullanım</span><span class="sxs-lookup"><span data-stu-id="61f03-134">Usage</span></span>

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="61f03-135">Konum:</span><span class="sxs-lookup"><span data-stu-id="61f03-135">Where:</span></span>

| <span data-ttu-id="61f03-136">Parametre</span><span class="sxs-lookup"><span data-stu-id="61f03-136">Parameter</span></span>         | <span data-ttu-id="61f03-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61f03-137">Description</span></span>                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | <span data-ttu-id="61f03-138">Sertifikanın konu adı</span><span class="sxs-lookup"><span data-stu-id="61f03-138">The subject name of the certificate</span></span>                                               |
| `<thumbprint>`  | <span data-ttu-id="61f03-139">Sertifikanın parmak izi (bunu bulmak için Certmgr.exe aracını kullanabilirsiniz)</span><span class="sxs-lookup"><span data-stu-id="61f03-139">The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)</span></span> |
| `-f`            | <span data-ttu-id="61f03-140">yalnızca çıkış dosyası adı</span><span class="sxs-lookup"><span data-stu-id="61f03-140">output file name only</span></span>                                                             |
| `-d`            | <span data-ttu-id="61f03-141">yalnızca çıkış dizini</span><span class="sxs-lookup"><span data-stu-id="61f03-141">output directory only</span></span>                                                             |
| `-a`            | <span data-ttu-id="61f03-142">çıkış mutlak dosya adı</span><span class="sxs-lookup"><span data-stu-id="61f03-142">output absolute file name</span></span>                                                         |

<span data-ttu-id="61f03-143">Komut isteminde hiçbir parametre belirtilmemişse, bu bilgileri içeren yardım metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="61f03-143">If no parameters are specified at the command prompt, then help text with this information is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="61f03-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="61f03-144">Examples</span></span>

<span data-ttu-id="61f03-145">Bu örnek, geçerli kullanıcının kişisel deposunda "CN = localhost" konu adına sahip sertifikanın dosya adını bulur.</span><span class="sxs-lookup"><span data-stu-id="61f03-145">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="61f03-146">Bu örnek, geçerli kullanıcının kişisel deposunda "CN = localhost" konu adına sahip sertifikanın dosya adını bulur ve tam dizin yolunu çıktı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="61f03-146">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="61f03-147">Bu örnek, yerel bilgisayarın Kişisel deposunda "03 33 98 63 D0 47 E7 48 71 33 62 64 76 5c 4c 9D 42 1D 6B 52" parmak izine sahip sertifikanın dosya adını bulur.</span><span class="sxs-lookup"><span data-stu-id="61f03-147">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
