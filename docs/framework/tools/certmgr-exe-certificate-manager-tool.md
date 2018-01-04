---
title: "Certmgr.exe (Sertifika Yönetim Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c303a9d91d12305bd8be4e111aaa8d6ac13eb77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="9bce1-102">Certmgr.exe (Sertifika Yönetim Aracı)</span><span class="sxs-lookup"><span data-stu-id="9bce1-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="9bce1-103">Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="9bce1-104">Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9bce1-105">Aracı'nı başlatmak için kullanmak [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9bce1-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bce1-106">Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="9bce1-107">Certmgr.msc genellikle Windows sistem dizininde bulduğundan girme `certmgr` Visual Studio komut istemi açılmış olsa bile, komut satırında sertifikalar MMC ek bileşenini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="9bce1-108">Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="9bce1-109">Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bce1-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="9bce1-110">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9bce1-111">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9bce1-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="9bce1-112">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9bce1-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="9bce1-113">X.509 sertifikaları genel bakış için bkz: [sertifikalarla çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9bce1-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="9bce1-114">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="9bce1-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bce1-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bce1-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bce1-116">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bce1-116">Parameters</span></span>  
  
|<span data-ttu-id="9bce1-117">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="9bce1-117">Argument</span></span>|<span data-ttu-id="9bce1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bce1-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9bce1-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="9bce1-119">*sourceStorename*</span></span>|<span data-ttu-id="9bce1-120">Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="9bce1-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="9bce1-121">Bu bir depo dosyası veya sistem deposu olabilir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="9bce1-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="9bce1-122">*destinationStorename*</span></span>|<span data-ttu-id="9bce1-123">Çıktı sertifika deposu veya dosyası.</span><span class="sxs-lookup"><span data-stu-id="9bce1-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="9bce1-124">Seçenek</span><span class="sxs-lookup"><span data-stu-id="9bce1-124">Option</span></span>|<span data-ttu-id="9bce1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bce1-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9bce1-126">**/ add**</span><span class="sxs-lookup"><span data-stu-id="9bce1-126">**/add**</span></span>|<span data-ttu-id="9bce1-127">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="9bce1-128">**/ all**</span><span class="sxs-lookup"><span data-stu-id="9bce1-128">**/all**</span></span>|<span data-ttu-id="9bce1-129">İle kullanıldığında tüm girişleri ekler **/ add**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="9bce1-130">İle kullanıldığında tüm girişleri siler **/del**. Olmadan kullanıldığında tüm girişleri görüntüler **/ add** veya **/del** seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="9bce1-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="9bce1-131">**/All** seçeneği birlikte kullanılamaz **/put**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="9bce1-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="9bce1-132">**/c**</span></span>|<span data-ttu-id="9bce1-133">İle kullanıldığında sertifikaları ekler **/ add**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="9bce1-134">İle kullanıldığında sertifikalarını siler **/del**. İle kullanıldığında sertifikaları kaydeder **/put**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="9bce1-135">Görüntüler olmadan kullanıldığında sertifikaları **/ add**, **/del**, veya **/put** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9bce1-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="9bce1-136">**/ CRL**</span><span class="sxs-lookup"><span data-stu-id="9bce1-136">**/CRL**</span></span>|<span data-ttu-id="9bce1-137">İle kullanıldığında CRL'ler ekler **/ add**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="9bce1-138">İle kullanıldığında CRL'ler siler **/del**. İle kullanıldığında CRL'ler kaydeder **/put**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="9bce1-139">Görüntüler olmadan kullanıldığında CRL'ler **/ add**, **/del**, veya **/put** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9bce1-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="9bce1-140">**/ CTL**</span><span class="sxs-lookup"><span data-stu-id="9bce1-140">**/CTL**</span></span>|<span data-ttu-id="9bce1-141">İle kullanıldığında CTL'ler ekler **/ add**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="9bce1-142">İle kullanıldığında CTL'ler siler **/del**. İle kullanıldığında CTL'ler kaydeder **/put**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="9bce1-143">Görüntüler olmadan kullanıldığında CTL'ler **/ add**, **/del**, veya **/put** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9bce1-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="9bce1-144">**/ DEL**</span><span class="sxs-lookup"><span data-stu-id="9bce1-144">**/del**</span></span>|<span data-ttu-id="9bce1-145">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="9bce1-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="9bce1-146">**/e** *encodingType*</span></span>|<span data-ttu-id="9bce1-147">Sertifika kodlama türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="9bce1-148">Varsayılan, `X509_ASN_ENCODING` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="9bce1-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="9bce1-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="9bce1-150">Depo açık bayrağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-150">Specifies the store open flag.</span></span> <span data-ttu-id="9bce1-151">Bu *dwFlags* parametresi geçirilen **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="9bce1-152">Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="9bce1-153">Bu seçenek, yalnızca olarak kabul edilir **/y** seçenek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9bce1-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="9bce1-154">**/h**[**ardım**]</span><span class="sxs-lookup"><span data-stu-id="9bce1-154">**/h**[**elp**]</span></span>|<span data-ttu-id="9bce1-155">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9bce1-156">**/n***adı*</span><span class="sxs-lookup"><span data-stu-id="9bce1-156">**/n** *nam*</span></span>|<span data-ttu-id="9bce1-157">Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="9bce1-158">Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9bce1-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="9bce1-159">**/ koyma**</span><span class="sxs-lookup"><span data-stu-id="9bce1-159">**/put**</span></span>|<span data-ttu-id="9bce1-160">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9bce1-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="9bce1-161">Dosya X.509 biçiminde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="9bce1-162">Kullanabileceğiniz **/7** seçeneğini **/put** seçeneği dosyayı PKCS #7 biçiminde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9bce1-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="9bce1-163">**/Put** seçeneği uyulması gerekir ya da **/c**, **/CTL**, veya **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="9bce1-164">**/All** seçeneği birlikte kullanılamaz **/put**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="9bce1-165">**/r** *konumu*</span><span class="sxs-lookup"><span data-stu-id="9bce1-165">**/r** *location*</span></span>|<span data-ttu-id="9bce1-166">Sistem deposu için kayıt defteri konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9bce1-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="9bce1-167">Bu seçenek yalnızca belirtirseniz kabul **/s** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9bce1-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="9bce1-168">*Konum* şunlardan biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9bce1-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="9bce1-169">-   `currentUser`Sertifika deposu HKEY_CURRENT_USER anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="9bce1-170">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9bce1-170">This is the default.</span></span><br /><span data-ttu-id="9bce1-171">-   `localMachine`Sertifika deposu HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="9bce1-172">**/ s**</span><span class="sxs-lookup"><span data-stu-id="9bce1-172">**/s**</span></span>|<span data-ttu-id="9bce1-173">Sertifika deposunun bir sistem deposu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="9bce1-174">Bu seçeneği belirtmezseniz, depo olarak kabul edilir bir **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="9bce1-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="9bce1-175">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="9bce1-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="9bce1-176">Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="9bce1-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="9bce1-177">**/v**</span></span>|<span data-ttu-id="9bce1-178">Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="9bce1-179">Bu seçenek kullanılamaz **/ add**, **/del**, veya **/put** seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="9bce1-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="9bce1-180">**/y** *sağlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="9bce1-180">**/y** *provider*</span></span>|<span data-ttu-id="9bce1-181">Depo sağlayıcısı adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bce1-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="9bce1-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="9bce1-182">**/7**</span></span>|<span data-ttu-id="9bce1-183">Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9bce1-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="9bce1-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="9bce1-184">**/?**</span></span>|<span data-ttu-id="9bce1-185">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bce1-186">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bce1-186">Remarks</span></span>  
 <span data-ttu-id="9bce1-187">Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9bce1-187">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="9bce1-188">Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="9bce1-189">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="9bce1-190">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="9bce1-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="9bce1-191">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9bce1-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="9bce1-192">Certmgr.exe iki tür sertifika depolarını çalışır: **StoreFile** ve sistem deposu.</span><span class="sxs-lookup"><span data-stu-id="9bce1-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="9bce1-193">Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="9bce1-194">Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir.</span><span class="sxs-lookup"><span data-stu-id="9bce1-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="9bce1-195">GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bce1-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="9bce1-196">X509Certificate depolarının adlarına bulabilirsiniz `sourceStorename` ve `destinationStorename` derleme ve aşağıdaki kodu çalıştırarak parametreleri.</span><span class="sxs-lookup"><span data-stu-id="9bce1-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="9bce1-197">Sertifikalar hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9bce1-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9bce1-198">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9bce1-198">Examples</span></span>  
 <span data-ttu-id="9bce1-199">Aşağıdaki komut adlı varsayılan sistem deposu görüntüler `my` ayrıntılı çıktıyla.</span><span class="sxs-lookup"><span data-stu-id="9bce1-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="9bce1-200">Aşağıdaki komut tüm sertifikaları adlı bir dosyaya ekler `myFile.ext` adlı yeni bir dosyaya `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="9bce1-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="9bce1-201">Aşağıdaki komut sertifikayı adındaki bir dosyada ekler `testcert.cer` için `my` sistem deposu.</span><span class="sxs-lookup"><span data-stu-id="9bce1-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="9bce1-202">Aşağıdaki komut sertifikayı adındaki bir dosyada ekler `TrustedCert.cer` kök sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="9bce1-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="9bce1-203">Aşağıdaki komut ortak ada sahip bir sertifika kaydeder `myCert` içinde `my` adlı bir dosya sistemi deposuna `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="9bce1-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="9bce1-204">Aşağıdaki komut, tüm CTL'ler siler `my` sistem deposu ve bir dosyaya sonuç deposu adlı kaydeder `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="9bce1-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="9bce1-205">Aşağıdaki komutu bir sertifikada kaydeder `my` dosya sistemi deposunda `newFile`.</span><span class="sxs-lookup"><span data-stu-id="9bce1-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="9bce1-206">Sertifika numarayı girin istenir `my` yerleştirmek için `newFile`.</span><span class="sxs-lookup"><span data-stu-id="9bce1-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bce1-207">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bce1-207">See Also</span></span>  
 [<span data-ttu-id="9bce1-208">Araçlar</span><span class="sxs-lookup"><span data-stu-id="9bce1-208">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="9bce1-209">MakeCert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="9bce1-209">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="9bce1-210">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="9bce1-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
