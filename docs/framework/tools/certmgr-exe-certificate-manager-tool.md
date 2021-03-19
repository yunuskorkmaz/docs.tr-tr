---
title: Certmgr.exe (Sertifika Yönetim Aracı)
description: Sertifika Yöneticisi aracını Certmgr.exe keşfedelim. Bu araç sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL 'Ler) yönetir.
ms.date: 03/30/2017
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
ms.openlocfilehash: eba8253a52f9dc533848fc7cbb76566c726495a2
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654199"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="54e01-104">Certmgr.exe (Sertifika Yönetim Aracı)</span><span class="sxs-lookup"><span data-stu-id="54e01-104">Certmgr.exe (Certificate Manager Tool)</span></span>

<span data-ttu-id="54e01-105">Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.</span><span class="sxs-lookup"><span data-stu-id="54e01-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="54e01-106">Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="54e01-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="54e01-107">Aracı başlatmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="54e01-107">To start the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54e01-108">Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="54e01-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="54e01-109">Certmgr. msc genellikle Windows sistem dizininde bulunduğu için, komut satırına girildiğinde, `certmgr` Visual Studio için geliştirici komut istemi açmış olsanız bile SERTIFIKALAR MMC ek bileşenini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e01-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="54e01-110">Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="54e01-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="54e01-111">Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e01-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>
  
 <span data-ttu-id="54e01-112">X. 509.440 sertifikalarına genel bakış için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="54e01-112">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="54e01-113">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="54e01-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e01-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54e01-114">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="54e01-115">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54e01-115">Parameters</span></span>  
  
|<span data-ttu-id="54e01-116">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="54e01-116">Argument</span></span>|<span data-ttu-id="54e01-117">Description</span><span class="sxs-lookup"><span data-stu-id="54e01-117">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="54e01-118">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="54e01-118">*sourceStorename*</span></span>|<span data-ttu-id="54e01-119">Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="54e01-119">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="54e01-120">Bu bir depo dosyası veya sistem deposu olabilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-120">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="54e01-121">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="54e01-121">*destinationStorename*</span></span>|<span data-ttu-id="54e01-122">Çıktı sertifika deposu veya dosyası.</span><span class="sxs-lookup"><span data-stu-id="54e01-122">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="54e01-123">Seçenek</span><span class="sxs-lookup"><span data-stu-id="54e01-123">Option</span></span>|<span data-ttu-id="54e01-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e01-124">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="54e01-125">**/Add**</span><span class="sxs-lookup"><span data-stu-id="54e01-125">**/add**</span></span>|<span data-ttu-id="54e01-126">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-126">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="54e01-127">**/All**</span><span class="sxs-lookup"><span data-stu-id="54e01-127">**/all**</span></span>|<span data-ttu-id="54e01-128">**/Add** ile kullanıldığında tüm girdileri ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-128">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="54e01-129">**/Del&lt** ile kullanıldığında tüm girdileri siler. **/Add** veya **/del&lt** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-129">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="54e01-130">**/All** seçeneği **/PUT** ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54e01-130">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="54e01-131">**/c**</span><span class="sxs-lookup"><span data-stu-id="54e01-131">**/c**</span></span>|<span data-ttu-id="54e01-132">**/Add** ile kullanıldığında sertifikaları ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-132">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="54e01-133">**/Del&lt** ile kullanıldığında sertifikaları siler. , **/PUT** ile kullanıldığında sertifikaları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-133">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="54e01-134">**/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında sertifikaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-134">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="54e01-135">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="54e01-135">**/CRL**</span></span>|<span data-ttu-id="54e01-136">**/Add** Ile kullanıldığında CRL 'leri ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-136">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="54e01-137">**/Del&lt** Ile kullanıldığında CRL 'leri siler. , **/PUT** Ile kullanıldığında CRL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-137">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="54e01-138">**/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında CRL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-138">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="54e01-139">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="54e01-139">**/CTL**</span></span>|<span data-ttu-id="54e01-140">**/Add** Ile kullanıldığında CTL ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-140">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="54e01-141">**/Del&lt** Ile kullanıldığında CTL 'leri siler. **/PUT** Ile kullanıldığında CTL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-141">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="54e01-142">**/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında CTL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-142">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="54e01-143">**/del&lt**</span><span class="sxs-lookup"><span data-stu-id="54e01-143">**/del**</span></span>|<span data-ttu-id="54e01-144">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="54e01-144">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="54e01-145">**/E** *EncodingType*</span><span class="sxs-lookup"><span data-stu-id="54e01-145">**/e** *encodingType*</span></span>|<span data-ttu-id="54e01-146">Sertifika kodlama türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e01-146">Specifies the certificate encoding type.</span></span> <span data-ttu-id="54e01-147">Varsayılan değer: `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="54e01-147">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="54e01-148">**/F** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="54e01-148">**/f** *dwFlags*</span></span>|<span data-ttu-id="54e01-149">Depo açık bayrağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e01-149">Specifies the store open flag.</span></span> <span data-ttu-id="54e01-150">Bu, **CertOpenStore**'A geçirilen *dwFlags* parametresidir.</span><span class="sxs-lookup"><span data-stu-id="54e01-150">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="54e01-151">Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir.</span><span class="sxs-lookup"><span data-stu-id="54e01-151">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="54e01-152">Bu seçenek yalnızca **/y** seçeneği kullanılırsa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-152">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="54e01-153">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="54e01-153">**/h**[**elp**]</span></span>|<span data-ttu-id="54e01-154">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-154">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="54e01-155">**/n** *Nam*</span><span class="sxs-lookup"><span data-stu-id="54e01-155">**/n** *nam*</span></span>|<span data-ttu-id="54e01-156">Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e01-156">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="54e01-157">Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54e01-157">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="54e01-158">**/Put**</span><span class="sxs-lookup"><span data-stu-id="54e01-158">**/put**</span></span>|<span data-ttu-id="54e01-159">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-159">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="54e01-160">Dosya X.509 biçiminde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-160">The file is saved in X.509 format.</span></span> <span data-ttu-id="54e01-161">Dosyayı PKCS #7 biçiminde kaydetmek için **/PUT** seçeneğiyle birlikte **/7** seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e01-161">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="54e01-162">**/PUT** seçeneğinin arkasından **/c**, **/CTL** veya **/CRL** gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="54e01-162">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="54e01-163">**/All** seçeneği **/PUT** ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54e01-163">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="54e01-164">**/r** *konumu*</span><span class="sxs-lookup"><span data-stu-id="54e01-164">**/r** *location*</span></span>|<span data-ttu-id="54e01-165">Sistem deposu için kayıt defteri konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54e01-165">Identifies the registry location of the system store.</span></span> <span data-ttu-id="54e01-166">Bu seçenek yalnızca **/s** seçeneğini belirtirseniz değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-166">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="54e01-167">*konum* aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="54e01-167">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="54e01-168">-   `currentUser` sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54e01-168">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="54e01-169">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="54e01-169">This is the default.</span></span><br /><span data-ttu-id="54e01-170">-   `localMachine` sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54e01-170">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="54e01-171">**sn**</span><span class="sxs-lookup"><span data-stu-id="54e01-171">**/s**</span></span>|<span data-ttu-id="54e01-172">Sertifika deposunun bir sistem deposu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54e01-172">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="54e01-173">Bu seçeneği belirtmezseniz, mağaza bir **StoreFile** olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-173">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="54e01-174">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="54e01-174">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="54e01-175">Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e01-175">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="54e01-176">**çıktıda**</span><span class="sxs-lookup"><span data-stu-id="54e01-176">**/v**</span></span>|<span data-ttu-id="54e01-177">Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-177">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="54e01-178">Bu seçenek **/Add**, **/del&lt** veya **/PUT** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="54e01-178">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="54e01-179">**/y** *sağlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="54e01-179">**/y** *provider*</span></span>|<span data-ttu-id="54e01-180">Depo sağlayıcısı adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="54e01-180">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="54e01-181">**/7**</span><span class="sxs-lookup"><span data-stu-id="54e01-181">**/7**</span></span>|<span data-ttu-id="54e01-182">Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-182">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="54e01-183">**/?**</span><span class="sxs-lookup"><span data-stu-id="54e01-183">**/?**</span></span>|<span data-ttu-id="54e01-184">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-184">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54e01-185">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54e01-185">Remarks</span></span>  

 <span data-ttu-id="54e01-186">Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="54e01-186">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="54e01-187">Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="54e01-187">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="54e01-188">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="54e01-188">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="54e01-189">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="54e01-189">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="54e01-190">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="54e01-190">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="54e01-191">Certmgr.exe, iki tür sertifika deposu ile birlikte kullanılabilir: **StoreFile** ve System Store.</span><span class="sxs-lookup"><span data-stu-id="54e01-191">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="54e01-192">Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="54e01-192">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="54e01-193">Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir.</span><span class="sxs-lookup"><span data-stu-id="54e01-193">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="54e01-194">GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.</span><span class="sxs-lookup"><span data-stu-id="54e01-194">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="54e01-195">`sourceStorename`Aşağıdaki kodu derleyerek ve çalıştırarak, ve parametreleri Için X509Certificate mağazaların adlarını bulabilirsiniz `destinationStorename` .</span><span class="sxs-lookup"><span data-stu-id="54e01-195">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="54e01-196">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="54e01-196">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="54e01-197">Örnekler</span><span class="sxs-lookup"><span data-stu-id="54e01-197">Examples</span></span>  

 <span data-ttu-id="54e01-198">Aşağıdaki komut, ayrıntılı çıktıyla çağrılan bir varsayılan sistem deposunu görüntüler `my` .</span><span class="sxs-lookup"><span data-stu-id="54e01-198">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="54e01-199">Aşağıdaki komut adlı bir dosyadaki tüm sertifikaları `myFile.ext` adlı yeni bir dosyaya ekler `newFile.ext` .</span><span class="sxs-lookup"><span data-stu-id="54e01-199">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="54e01-200">Aşağıdaki komut, sertifikayı sistem deposuna adlı bir dosyaya ekler `testcert.cer` `my` .</span><span class="sxs-lookup"><span data-stu-id="54e01-200">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="54e01-201">Aşağıdaki komut, sertifikayı Kök sertifika deposuna adlı bir dosyaya ekler `TrustedCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="54e01-201">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="54e01-202">Aşağıdaki komut, sistem deposunda ortak ada sahip bir sertifikayı `myCert` `my` adlı bir dosyaya kaydeder `newCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="54e01-202">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="54e01-203">Aşağıdaki komut, sistem deposundaki tüm CTL 'leri siler `my` ve elde edilen depoyu adlı bir dosyaya kaydeder `newStore.str` .</span><span class="sxs-lookup"><span data-stu-id="54e01-203">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="54e01-204">Aşağıdaki komut, bir sertifikayı `my` dosyadaki sistem deposuna kaydeder `newFile` .</span><span class="sxs-lookup"><span data-stu-id="54e01-204">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="54e01-205">İçine koymak için sertifika numarasını girmeniz istenir `my` `newFile` .</span><span class="sxs-lookup"><span data-stu-id="54e01-205">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="54e01-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e01-206">See also</span></span>

- [<span data-ttu-id="54e01-207">Araçlar</span><span class="sxs-lookup"><span data-stu-id="54e01-207">Tools</span></span>](index.md)
- [<span data-ttu-id="54e01-208">Makecert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="54e01-208">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="54e01-209">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="54e01-209">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
