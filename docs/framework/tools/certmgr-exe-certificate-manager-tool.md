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
ms.openlocfilehash: 43ab281e6ec28ff23ea584b03fd4278c6682e33e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167271"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="2a346-104">Certmgr.exe (Sertifika Yönetim Aracı)</span><span class="sxs-lookup"><span data-stu-id="2a346-104">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="2a346-105">Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.</span><span class="sxs-lookup"><span data-stu-id="2a346-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="2a346-106">Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2a346-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2a346-107">Aracı başlatmak için [komut istemlerini](developer-command-prompt-for-vs.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a346-107">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a346-108">Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="2a346-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="2a346-109">Certmgr. msc genellikle Windows sistem dizininde bulunduğu için, komut satırına girildiğinde, `certmgr` Visual Studio için geliştirici komut istemi açmış olsanız bile SERTIFIKALAR MMC ek bileşenini yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a346-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2a346-110">Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2a346-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="2a346-111">Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a346-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="2a346-112">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2a346-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2a346-113">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a346-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2a346-114">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2a346-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2a346-115">X. 509.440 sertifikalarına genel bakış için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2a346-115">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="2a346-116">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="2a346-116">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a346-117">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2a346-117">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a346-118">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a346-118">Parameters</span></span>  
  
|<span data-ttu-id="2a346-119">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="2a346-119">Argument</span></span>|<span data-ttu-id="2a346-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a346-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2a346-121">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="2a346-121">*sourceStorename*</span></span>|<span data-ttu-id="2a346-122">Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2a346-122">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="2a346-123">Bu bir depo dosyası veya sistem deposu olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-123">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="2a346-124">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="2a346-124">*destinationStorename*</span></span>|<span data-ttu-id="2a346-125">Çıktı sertifika deposu veya dosyası.</span><span class="sxs-lookup"><span data-stu-id="2a346-125">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="2a346-126">Seçenek</span><span class="sxs-lookup"><span data-stu-id="2a346-126">Option</span></span>|<span data-ttu-id="2a346-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a346-127">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2a346-128">**/Add**</span><span class="sxs-lookup"><span data-stu-id="2a346-128">**/add**</span></span>|<span data-ttu-id="2a346-129">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-129">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="2a346-130">**/All**</span><span class="sxs-lookup"><span data-stu-id="2a346-130">**/all**</span></span>|<span data-ttu-id="2a346-131">**/Add**ile kullanıldığında tüm girdileri ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-131">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="2a346-132">**/Del&lt**ile kullanıldığında tüm girdileri siler. **/Add** veya **/del&lt** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-132">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="2a346-133">**/All** seçeneği **/PUT**ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a346-133">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2a346-134">**/c**</span><span class="sxs-lookup"><span data-stu-id="2a346-134">**/c**</span></span>|<span data-ttu-id="2a346-135">**/Add**ile kullanıldığında sertifikaları ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-135">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="2a346-136">**/Del&lt**ile kullanıldığında sertifikaları siler. , **/PUT**ile kullanıldığında sertifikaları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-136">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="2a346-137">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında sertifikaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a346-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="2a346-138">**/CRL**</span></span>|<span data-ttu-id="2a346-139">**/Add**Ile kullanıldığında CRL 'leri ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="2a346-140">**/Del&lt**Ile kullanıldığında CRL 'leri siler. , **/PUT**Ile kullanıldığında CRL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-140">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="2a346-141">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CRL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-141">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a346-142">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="2a346-142">**/CTL**</span></span>|<span data-ttu-id="2a346-143">**/Add**Ile kullanıldığında CTL ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-143">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="2a346-144">**/Del&lt**Ile kullanıldığında CTL 'leri siler. **/PUT**Ile kullanıldığında CTL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-144">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="2a346-145">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CTL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-145">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2a346-146">**/del&lt**</span><span class="sxs-lookup"><span data-stu-id="2a346-146">**/del**</span></span>|<span data-ttu-id="2a346-147">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="2a346-147">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="2a346-148">**/E** *EncodingType*</span><span class="sxs-lookup"><span data-stu-id="2a346-148">**/e** *encodingType*</span></span>|<span data-ttu-id="2a346-149">Sertifika kodlama türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a346-149">Specifies the certificate encoding type.</span></span> <span data-ttu-id="2a346-150">Varsayılan değer: `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="2a346-150">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="2a346-151">**/F** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="2a346-151">**/f** *dwFlags*</span></span>|<span data-ttu-id="2a346-152">Depo açık bayrağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a346-152">Specifies the store open flag.</span></span> <span data-ttu-id="2a346-153">Bu, **CertOpenStore**'A geçirilen *dwFlags* parametresidir.</span><span class="sxs-lookup"><span data-stu-id="2a346-153">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="2a346-154">Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir.</span><span class="sxs-lookup"><span data-stu-id="2a346-154">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="2a346-155">Bu seçenek yalnızca **/y** seçeneği kullanılırsa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-155">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="2a346-156">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="2a346-156">**/h**[**elp**]</span></span>|<span data-ttu-id="2a346-157">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-157">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2a346-158">**/n** *Nam*</span><span class="sxs-lookup"><span data-stu-id="2a346-158">**/n** *nam*</span></span>|<span data-ttu-id="2a346-159">Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a346-159">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="2a346-160">Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a346-160">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="2a346-161">**/Put**</span><span class="sxs-lookup"><span data-stu-id="2a346-161">**/put**</span></span>|<span data-ttu-id="2a346-162">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-162">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="2a346-163">Dosya X.509 biçiminde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-163">The file is saved in X.509 format.</span></span> <span data-ttu-id="2a346-164">Dosyayı PKCS #7 biçiminde kaydetmek için **/PUT** seçeneğiyle birlikte **/7** seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a346-164">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="2a346-165">**/PUT** seçeneğinin arkasından **/c**, **/CTL**veya **/CRL**gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="2a346-165">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="2a346-166">**/All** seçeneği **/PUT**ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a346-166">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2a346-167">**/r** *konumu*</span><span class="sxs-lookup"><span data-stu-id="2a346-167">**/r** *location*</span></span>|<span data-ttu-id="2a346-168">Sistem deposu için kayıt defteri konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a346-168">Identifies the registry location of the system store.</span></span> <span data-ttu-id="2a346-169">Bu seçenek yalnızca **/s** seçeneğini belirtirseniz değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-169">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="2a346-170">*konum* aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2a346-170">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="2a346-171">-   `currentUser`sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a346-171">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="2a346-172">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="2a346-172">This is the default.</span></span><br /><span data-ttu-id="2a346-173">-   `localMachine`sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a346-173">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="2a346-174">**sn**</span><span class="sxs-lookup"><span data-stu-id="2a346-174">**/s**</span></span>|<span data-ttu-id="2a346-175">Sertifika deposunun bir sistem deposu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a346-175">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="2a346-176">Bu seçeneği belirtmezseniz, mağaza bir **StoreFile**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-176">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="2a346-177">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="2a346-177">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="2a346-178">Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a346-178">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="2a346-179">**çıktıda**</span><span class="sxs-lookup"><span data-stu-id="2a346-179">**/v**</span></span>|<span data-ttu-id="2a346-180">Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-180">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="2a346-181">Bu seçenek **/Add**, **/del&lt**veya **/PUT** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a346-181">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="2a346-182">**/y** *sağlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="2a346-182">**/y** *provider*</span></span>|<span data-ttu-id="2a346-183">Depo sağlayıcısı adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a346-183">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="2a346-184">**/7**</span><span class="sxs-lookup"><span data-stu-id="2a346-184">**/7**</span></span>|<span data-ttu-id="2a346-185">Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-185">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="2a346-186">**/?**</span><span class="sxs-lookup"><span data-stu-id="2a346-186">**/?**</span></span>|<span data-ttu-id="2a346-187">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-187">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a346-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a346-188">Remarks</span></span>  
 <span data-ttu-id="2a346-189">Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="2a346-189">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="2a346-190">Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a346-190">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="2a346-191">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="2a346-191">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="2a346-192">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="2a346-192">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="2a346-193">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2a346-193">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="2a346-194">Certmgr.exe, iki tür sertifika deposu ile birlikte kullanılabilir: **StoreFile** ve System Store.</span><span class="sxs-lookup"><span data-stu-id="2a346-194">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="2a346-195">Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2a346-195">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="2a346-196">Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir.</span><span class="sxs-lookup"><span data-stu-id="2a346-196">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="2a346-197">GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a346-197">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="2a346-198">`sourceStorename`Aşağıdaki kodu derleyerek ve çalıştırarak, ve parametreleri Için X509Certificate mağazaların adlarını bulabilirsiniz `destinationStorename` .</span><span class="sxs-lookup"><span data-stu-id="2a346-198">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="2a346-199">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2a346-199">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2a346-200">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2a346-200">Examples</span></span>  
 <span data-ttu-id="2a346-201">Aşağıdaki komut, ayrıntılı çıktıyla çağrılan bir varsayılan sistem deposunu görüntüler `my` .</span><span class="sxs-lookup"><span data-stu-id="2a346-201">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="2a346-202">Aşağıdaki komut adlı bir dosyadaki tüm sertifikaları `myFile.ext` adlı yeni bir dosyaya ekler `newFile.ext` .</span><span class="sxs-lookup"><span data-stu-id="2a346-202">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="2a346-203">Aşağıdaki komut, sertifikayı sistem deposuna adlı bir dosyaya ekler `testcert.cer` `my` .</span><span class="sxs-lookup"><span data-stu-id="2a346-203">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="2a346-204">Aşağıdaki komut, sertifikayı Kök sertifika deposuna adlı bir dosyaya ekler `TrustedCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="2a346-204">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="2a346-205">Aşağıdaki komut, sistem deposunda ortak ada sahip bir sertifikayı `myCert` `my` adlı bir dosyaya kaydeder `newCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="2a346-205">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="2a346-206">Aşağıdaki komut, sistem deposundaki tüm CTL 'leri siler `my` ve elde edilen depoyu adlı bir dosyaya kaydeder `newStore.str` .</span><span class="sxs-lookup"><span data-stu-id="2a346-206">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="2a346-207">Aşağıdaki komut, bir sertifikayı `my` dosyadaki sistem deposuna kaydeder `newFile` .</span><span class="sxs-lookup"><span data-stu-id="2a346-207">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="2a346-208">İçine koymak için sertifika numarasını girmeniz istenir `my` `newFile` .</span><span class="sxs-lookup"><span data-stu-id="2a346-208">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a346-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a346-209">See also</span></span>

- [<span data-ttu-id="2a346-210">Araçlar</span><span class="sxs-lookup"><span data-stu-id="2a346-210">Tools</span></span>](index.md)
- [<span data-ttu-id="2a346-211">Makecert.exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="2a346-211">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="2a346-212">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="2a346-212">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
