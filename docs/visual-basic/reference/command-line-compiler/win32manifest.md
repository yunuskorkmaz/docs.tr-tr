---
title: /win32manifest (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a46641181c3ff66882468f8372bb97c3a49a8462
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="win32manifest-visual-basic"></a><span data-ttu-id="82c8e-102">/win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82c8e-102">/win32manifest (Visual Basic)</span></span>
<span data-ttu-id="82c8e-103">Bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılmış bir kullanıcı tarafından tanımlanan Win32 uygulama bildirim dosyasının tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82c8e-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82c8e-104">Syntax</span></span>  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="82c8e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="82c8e-105">Arguments</span></span>  
  
|<span data-ttu-id="82c8e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="82c8e-106">Term</span></span>|<span data-ttu-id="82c8e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="82c8e-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="82c8e-108">Özel bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="82c8e-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82c8e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82c8e-109">Remarks</span></span>  
 <span data-ttu-id="82c8e-110">Varsayılan olarak, Visual Basic derleyici asInvoker istenen yürütme düzeyini belirten bir uygulama bildirimi katıştırır.</span><span class="sxs-lookup"><span data-stu-id="82c8e-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="82c8e-111">Hangi yürütülebilir dosya yapılandırıldığında, genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82c8e-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="82c8e-112">Örneğin highestAvailable veya requireAdministrator istenen yürütme düzeyini belirtmek özel bir bildirimi sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="82c8e-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82c8e-113">Bu seçenek ve [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) seçeneği karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="82c8e-113">This option and the [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="82c8e-114">Her iki seçenek aynı komut satırında kullanmaya çalışırsa, bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="82c8e-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="82c8e-115">Hiçbir uygulama bildirimini olan bir uygulama, istenen yürütme düzeyinin Windows Vista kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırma tabi olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="82c8e-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="82c8e-116">Sanallaştırma hakkında daha fazla bilgi için bkz: [Windows Vista'da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="82c8e-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="82c8e-117">Aşağıdaki koşullardan biri doğru olduğunda, uygulamanızın sanallaştırma tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="82c8e-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="82c8e-118">Kullandığınız `/nowin32manifest` seçeneğini sağlamaz daha yeni bir derleme adımı veya Windows Kaynak (.res) dosyasının bir parçası olarak bir bildirim kullanarak `/win32resource` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="82c8e-118">You use the `/nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `/win32resource` option.</span></span>  
  
2.  <span data-ttu-id="82c8e-119">İstenen yürütme düzeyinin belirtmiyor özel bir bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="82c8e-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="82c8e-120">Varsayılan bir .manifest dosyası oluşturur ve yürütülebilir dosyanın yanında hata ayıklama ve yayın dizinleri depolar.</span><span class="sxs-lookup"><span data-stu-id="82c8e-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="82c8e-121">Görüntülemek veya tıklayarak varsayılan app.manifest dosyasını düzenleyin **görünümü UAC ayarları** üzerinde **uygulama** Proje Tasarımcısı'nda sekmesi.</span><span class="sxs-lookup"><span data-stu-id="82c8e-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="82c8e-122">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="82c8e-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="82c8e-123">Kullanarak oluşturma sonrası özel bir adım veya Win32 kaynak dosyasını bir parçası olarak uygulama bildirimini sağlayabilirsiniz `/nowin32manifest` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="82c8e-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `/nowin32manifest` option.</span></span> <span data-ttu-id="82c8e-124">Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız aynı seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="82c8e-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="82c8e-125">Bu oluşturma ve varsayılan bildirimini PE'yi dosyasında katıştırma derleyici engeller.</span><span class="sxs-lookup"><span data-stu-id="82c8e-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c8e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="82c8e-126">Example</span></span>  
 <span data-ttu-id="82c8e-127">Aşağıdaki örnek, Visual Basic derleyici bir PE'ye eklediği varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="82c8e-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82c8e-128">Derleyici standart uygulama adı MyApplication.app XML bildirimine ekler.</span><span class="sxs-lookup"><span data-stu-id="82c8e-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="82c8e-129">Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını etkinleştirmek için bir çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="82c8e-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82c8e-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82c8e-130">See Also</span></span>  
 [<span data-ttu-id="82c8e-131">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="82c8e-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="82c8e-132">/ nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82c8e-132">/nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
