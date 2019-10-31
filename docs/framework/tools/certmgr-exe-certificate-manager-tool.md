---
title: Certmgr.exe (Sertifika Yönetim Aracı)
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
ms.openlocfilehash: 06fe3a78d0b19720d4f83111980b88806312205f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129870"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="0ca32-102">Certmgr.exe (Sertifika Yönetim Aracı)</span><span class="sxs-lookup"><span data-stu-id="0ca32-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="0ca32-103">Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="0ca32-104">Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0ca32-105">Aracı başlatmak için [komut istemlerini](developer-command-prompt-for-vs.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ca32-105">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca32-106">Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="0ca32-107">Certmgr. msc genellikle Windows sistem dizininde bulunduğu için, komut satırına `certmgr` girilmesi, Visual Studio Geliştirici Komut İstemi açmış olsanız bile Sertifikalar MMC ek bileşenini yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="0ca32-108">Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="0ca32-109">Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="0ca32-110">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0ca32-111">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ca32-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="0ca32-112">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0ca32-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="0ca32-113">X. 509.440 sertifikalarına genel bakış için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0ca32-113">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="0ca32-114">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="0ca32-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca32-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ca32-115">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ca32-116">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ca32-116">Parameters</span></span>  
  
|<span data-ttu-id="0ca32-117">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="0ca32-117">Argument</span></span>|<span data-ttu-id="0ca32-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca32-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="0ca32-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="0ca32-119">*sourceStorename*</span></span>|<span data-ttu-id="0ca32-120">Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="0ca32-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="0ca32-121">Bu bir depo dosyası veya sistem deposu olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="0ca32-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="0ca32-122">*destinationStorename*</span></span>|<span data-ttu-id="0ca32-123">Çıktı sertifika deposu veya dosyası.</span><span class="sxs-lookup"><span data-stu-id="0ca32-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="0ca32-124">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0ca32-124">Option</span></span>|<span data-ttu-id="0ca32-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca32-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0ca32-126">**/Add**</span><span class="sxs-lookup"><span data-stu-id="0ca32-126">**/add**</span></span>|<span data-ttu-id="0ca32-127">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="0ca32-128">**/All**</span><span class="sxs-lookup"><span data-stu-id="0ca32-128">**/all**</span></span>|<span data-ttu-id="0ca32-129">**/Add**ile kullanıldığında tüm girdileri ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="0ca32-130">**/Del&lt**ile kullanıldığında tüm girdileri siler. **/Add** veya **/del&lt** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="0ca32-131">**/All** seçeneği **/PUT**ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="0ca32-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="0ca32-132">**/c**</span></span>|<span data-ttu-id="0ca32-133">**/Add**ile kullanıldığında sertifikaları ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="0ca32-134">**/Del&lt**ile kullanıldığında sertifikaları siler. , **/PUT**ile kullanıldığında sertifikaları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="0ca32-135">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında sertifikaları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="0ca32-136">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="0ca32-136">**/CRL**</span></span>|<span data-ttu-id="0ca32-137">**/Add**Ile kullanıldığında CRL 'leri ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="0ca32-138">**/Del&lt**Ile kullanıldığında CRL 'leri siler. , **/PUT**Ile kullanıldığında CRL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="0ca32-139">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CRL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="0ca32-140">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="0ca32-140">**/CTL**</span></span>|<span data-ttu-id="0ca32-141">**/Add**Ile kullanıldığında CTL ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="0ca32-142">**/Del&lt**Ile kullanıldığında CTL 'leri siler. **/PUT**Ile kullanıldığında CTL 'leri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="0ca32-143">**/Add**, **/del&lt**veya **/PUT** seçeneği olmadan kullanıldığında CTL 'leri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="0ca32-144">**/del&lt**</span><span class="sxs-lookup"><span data-stu-id="0ca32-144">**/del**</span></span>|<span data-ttu-id="0ca32-145">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="0ca32-146">**/E** *EncodingType*</span><span class="sxs-lookup"><span data-stu-id="0ca32-146">**/e** *encodingType*</span></span>|<span data-ttu-id="0ca32-147">Sertifika kodlama türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="0ca32-148">Varsayılan, `X509_ASN_ENCODING` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="0ca32-149">**/F** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="0ca32-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="0ca32-150">Depo açık bayrağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-150">Specifies the store open flag.</span></span> <span data-ttu-id="0ca32-151">Bu, **CertOpenStore**'A geçirilen *dwFlags* parametresidir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="0ca32-152">Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="0ca32-153">Bu seçenek yalnızca **/y** seçeneği kullanılırsa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="0ca32-154">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="0ca32-154">**/h**[**elp**]</span></span>|<span data-ttu-id="0ca32-155">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="0ca32-156">**/n** *Nam*</span><span class="sxs-lookup"><span data-stu-id="0ca32-156">**/n** *nam*</span></span>|<span data-ttu-id="0ca32-157">Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="0ca32-158">Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="0ca32-159">**/Put**</span><span class="sxs-lookup"><span data-stu-id="0ca32-159">**/put**</span></span>|<span data-ttu-id="0ca32-160">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="0ca32-161">Dosya X.509 biçiminde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="0ca32-162">Dosyayı PKCS #7 biçiminde kaydetmek için **/PUT** seçeneğiyle birlikte **/7** seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="0ca32-163">**/PUT** seçeneğinin arkasından **/c**, **/CTL**veya **/CRL**gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="0ca32-164">**/All** seçeneği **/PUT**ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="0ca32-165">**/r** *konumu*</span><span class="sxs-lookup"><span data-stu-id="0ca32-165">**/r** *location*</span></span>|<span data-ttu-id="0ca32-166">Sistem deposu için kayıt defteri konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ca32-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="0ca32-167">Bu seçenek yalnızca **/s** seçeneğini belirtirseniz değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="0ca32-168">*konum* aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="0ca32-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="0ca32-169">-   `currentUser`, sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="0ca32-170">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0ca32-170">This is the default.</span></span><br /><span data-ttu-id="0ca32-171">-   `localMachine`, sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="0ca32-172">**sn**</span><span class="sxs-lookup"><span data-stu-id="0ca32-172">**/s**</span></span>|<span data-ttu-id="0ca32-173">Sertifika deposunun bir sistem deposu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="0ca32-174">Bu seçeneği belirtmezseniz, mağaza bir **StoreFile**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="0ca32-175">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="0ca32-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="0ca32-176">Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="0ca32-177">**çıktıda**</span><span class="sxs-lookup"><span data-stu-id="0ca32-177">**/v**</span></span>|<span data-ttu-id="0ca32-178">Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="0ca32-179">Bu seçenek **/Add**, **/del&lt**veya **/PUT** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="0ca32-180">**/y** *sağlayıcısı*</span><span class="sxs-lookup"><span data-stu-id="0ca32-180">**/y** *provider*</span></span>|<span data-ttu-id="0ca32-181">Depo sağlayıcısı adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca32-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="0ca32-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="0ca32-182">**/7**</span></span>|<span data-ttu-id="0ca32-183">Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="0ca32-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="0ca32-184">**/?**</span></span>|<span data-ttu-id="0ca32-185">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca32-186">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ca32-186">Remarks</span></span>  
 <span data-ttu-id="0ca32-187">Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="0ca32-187">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="0ca32-188">Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="0ca32-189">Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="0ca32-190">Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="0ca32-191">Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="0ca32-192">Certmgr. exe iki tür sertifika deposu ile birlikte kullanılabilir: **StoreFile** ve System Store.</span><span class="sxs-lookup"><span data-stu-id="0ca32-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="0ca32-193">Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="0ca32-194">Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="0ca32-195">GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca32-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="0ca32-196">Aşağıdaki kodu derleyerek ve çalıştırarak `sourceStorename` ve `destinationStorename` parametreleri için X509Certificate mağazaların adlarını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="0ca32-197">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0ca32-197">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0ca32-198">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0ca32-198">Examples</span></span>  
 <span data-ttu-id="0ca32-199">Aşağıdaki komut, ayrıntılı çıktıyla `my` adlı varsayılan bir sistem deposunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="0ca32-200">Aşağıdaki komut, `myFile.ext` adlı bir dosyadaki tüm sertifikaları `newFile.ext`adlı yeni bir dosyaya ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="0ca32-201">Aşağıdaki komut, sertifikayı `my` sistem deposuna `testcert.cer` adlı bir dosyaya ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="0ca32-202">Aşağıdaki komut, sertifikayı Kök sertifika deposuna `TrustedCert.cer` adlı bir dosyaya ekler.</span><span class="sxs-lookup"><span data-stu-id="0ca32-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="0ca32-203">Aşağıdaki komut, `my` sistem deposundaki `myCert` ortak ada sahip bir sertifikayı `newCert.cer`adlı bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="0ca32-204">Aşağıdaki komut `my` sistem deposundaki tüm CTL 'leri siler ve elde edilen depoyu `newStore.str`adlı bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="0ca32-205">Aşağıdaki komut, bir sertifikayı dosya `newFile``my` sistem deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ca32-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="0ca32-206">`newFile`koymak için `my` sertifika numarasını girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="0ca32-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ca32-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca32-207">See also</span></span>

- [<span data-ttu-id="0ca32-208">Araçlar</span><span class="sxs-lookup"><span data-stu-id="0ca32-208">Tools</span></span>](index.md)
- [<span data-ttu-id="0ca32-209">MakeCert. exe (sertifika oluşturma aracı)</span><span class="sxs-lookup"><span data-stu-id="0ca32-209">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="0ca32-210">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="0ca32-210">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
