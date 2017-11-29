---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="23cd5-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="23cd5-102">FindPrivateKey</span></span>
<span data-ttu-id="23cd5-103">Belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="23cd5-104">FindPrivateKey.exe aracı bu işlemi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="23cd5-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="23cd5-105">FindPrivateKey kullanmak için derlenmiş önceki olması gereken bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="23cd5-106">FindPrivateKey aracı derleme hakkında yönergeler için aşağıdaki "FindPrivateKey projeyi oluşturmak için" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23cd5-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="23cd5-107">X.509 sertifikaları, bir yönetici veya makinede herhangi bir kullanıcı tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="23cd5-108">Ancak sertifika başka bir hesap altında çalışan bir hizmete erişebilir (örneğin, ASP.NET üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya ağ hizmeti hesaplarında [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="23cd5-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="23cd5-109">Sertifika tarafından başlangıçta yüklenmediğinden bu hesap için özel anahtar dosyası erişimi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="23cd5-110">FindPrivateKey aracı bir verilen X.509 sertifikasının özel anahtar dosyasının konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="23cd5-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="23cd5-111">İzinleri eklemek veya bu dosyaya izinleri belirli X.509 sertifikalarının özel anahtar dosyasının konumunu öğrendikten sonra kaldırın.</span><span class="sxs-lookup"><span data-stu-id="23cd5-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="23cd5-112">Güvenlik için sertifikaları kullanma örnekleri Setup.bat dosyasında FindPrivateKey aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="23cd5-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="23cd5-113">Özel anahtar dosyası bulunamadı sonra uygun erişim haklarını dosyanın ayarlamak için Cacls.exe gibi diğer araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23cd5-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="23cd5-114">Çalıştırırken bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kendini barındıran bir yürütülebilir dosya gibi bir kullanıcı hesabı altında service, kullanıcı hesabının dosyaya salt okunur erişim bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="23cd5-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="23cd5-115">Çalıştırırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altında Internet Information Services (hizmetinin altında çalıştığı için varsayılan hesaplar olan ASPNET IIS) hizmetini [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya ağ hizmeti üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], varsayılan olarak erişimi yoktur özel anahtar dosyası.</span><span class="sxs-lookup"><span data-stu-id="23cd5-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="23cd5-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="23cd5-116">Examples</span></span>  
 <span data-ttu-id="23cd5-117">İşlemi okuma ayrıcalığı olmayan bir sertifika erişirken, aşağıdaki örneğe benzer bir özel durum iletisi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="23cd5-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="23cd5-118">Bu durumda özel anahtar dosyasını bulun ve ardından sağ hizmetinin altında çalışan işlemi için erişim için FindPrivateKey aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="23cd5-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="23cd5-119">Örneğin, bu Cacls.exe aracıyla aşağıdaki örnekte gösterildiği gibi yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="23cd5-120">FindPrivateKey projeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="23cd5-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="23cd5-121">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] ve örnek yüklendiği dizin konumu altında dile özgü alt dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="23cd5-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="23cd5-122">Visual Studio'da dosyayı açmaya .sln dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="23cd5-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="23cd5-123">İçinde **yapı** menüsünde, select **çözümü yeniden derle**.</span><span class="sxs-lookup"><span data-stu-id="23cd5-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="23cd5-124">İstemci program dosyaları için client\bin yerleşiktir ve hizmet program dosyaları için service\bin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="23cd5-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="23cd5-125">Çözümü derleme dosyası oluşturur: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="23cd5-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="23cd5-126">Kuralları — komut satırı girişleri</span><span class="sxs-lookup"><span data-stu-id="23cd5-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="23cd5-127">"[*seçeneği*]" bir isteğe bağlı parametreleri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23cd5-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="23cd5-128">"{*seçeneği*}" parametreleri zorunlu kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23cd5-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="23cd5-129">"*seçenek 1* &#124; *Seçenek2*"seçenekleri kümesi arasında bir seçim temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23cd5-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="23cd5-130">"\<*değeri*>" girilecek bir parametre değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23cd5-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="23cd5-131">Kullanım</span><span class="sxs-lookup"><span data-stu-id="23cd5-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="23cd5-132">Konum:</span><span class="sxs-lookup"><span data-stu-id="23cd5-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="23cd5-133">Komut isteminde hiçbir parametre belirtilmezse, bu Yardım metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="23cd5-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="23cd5-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="23cd5-134">Examples</span></span>  
 <span data-ttu-id="23cd5-135">Bu örnek sertifika filename konu adıyla bulur "CN = localhost", kişisel deposunda geçerli User.FindPrivateKey My Currentuser'a - n "CN = localhost".</span><span class="sxs-lookup"><span data-stu-id="23cd5-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="23cd5-136">Bu örnek sertifika filename konu adıyla bulur "CN = localhost", Kişisel depolama geçerli ve tam dizin yolu çıktı.</span><span class="sxs-lookup"><span data-stu-id="23cd5-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="23cd5-137">Bu örnek dosya adının sertifikanın parmak izi bulur "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", yerel bilgisayarın kişisel deposunda.</span><span class="sxs-lookup"><span data-stu-id="23cd5-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="23cd5-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23cd5-138">See Also</span></span>
