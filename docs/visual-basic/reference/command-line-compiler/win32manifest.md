---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349137"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="e1986-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1986-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="e1986-103">Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1986-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1986-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1986-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1986-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e1986-105">Arguments</span></span>  
  
|<span data-ttu-id="e1986-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e1986-106">Term</span></span>|<span data-ttu-id="e1986-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e1986-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="e1986-108">Özel bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e1986-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1986-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1986-109">Remarks</span></span>  
 <span data-ttu-id="e1986-110">Varsayılan olarak Visual Basic derleyici, istenen bir yürütme düzeyi olan asInvoker belirten bir uygulama bildirimi katıştırır.</span><span class="sxs-lookup"><span data-stu-id="e1986-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="e1986-111">Bu, bildirim, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e1986-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="e1986-112">Özel bir bildirim sağlamak istiyorsanız, örneğin, bir highestAvailable veya requireAdministrator istenen yürütme düzeyini belirtmek için bu seçeneği, dosyanın adını belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1986-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1986-113">Bu seçenek ve [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) seçeneği birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="e1986-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="e1986-114">Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e1986-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="e1986-115">İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows Vista 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir.</span><span class="sxs-lookup"><span data-stu-id="e1986-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="e1986-116">Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="e1986-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="e1986-117">Aşağıdaki koşullardan biri doğru ise uygulamanız sanallaştırmaya tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="e1986-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="e1986-118">`-nowin32manifest` seçeneğini kullanın ve `-win32resource` seçeneğini kullanarak bir sonraki derleme adımında veya Windows kaynak (. res) dosyasının bir parçası olarak bir bildirim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e1986-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="e1986-119">İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e1986-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="e1986-120">Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar.</span><span class="sxs-lookup"><span data-stu-id="e1986-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="e1986-121">Varsayılan App. manifest dosyasını, proje Tasarımcısı 'ndaki **uygulama** sekmesinde **UAC ayarlarını görüntüle** ' ye tıklayarak görüntüleyebilir veya düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1986-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="e1986-122">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e1986-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="e1986-123">Uygulama bildirimini, bir derleme sonrası özel adım olarak veya `-nowin32manifest` seçeneğini kullanarak bir Win32 kaynak dosyasının parçası olarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1986-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="e1986-124">Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1986-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="e1986-125">Bu, derleyicinin PE dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="e1986-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1986-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1986-126">Example</span></span>  
 <span data-ttu-id="e1986-127">Aşağıdaki örnek, Visual Basic derleyicisinin bir PE 'ye eklediği varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1986-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1986-128">Derleyici, bildirim XML dosyasına bir standart uygulama adı MyApplication. uygulaması ekler.</span><span class="sxs-lookup"><span data-stu-id="e1986-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="e1986-129">Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="e1986-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1986-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1986-130">See also</span></span>

- [<span data-ttu-id="e1986-131">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e1986-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e1986-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1986-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
