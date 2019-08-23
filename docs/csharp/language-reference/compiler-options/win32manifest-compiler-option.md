---
title: -win32manifest (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924682"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="da325-102">-win32manifest (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="da325-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="da325-103">Bir projenin Taşınabilir çalıştırılabilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası belirtmek için **-win32manifest** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="da325-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da325-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="da325-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="da325-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="da325-106">Özel bildirim dosyasının adı ve konumu.</span><span class="sxs-lookup"><span data-stu-id="da325-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da325-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da325-107">Remarks</span></span>  
 <span data-ttu-id="da325-108">Varsayılan olarak, görsel C# derleyici Istenen "asInvoker" yürütme düzeyini belirten bir uygulama bildirimi katıştırır.</span><span class="sxs-lookup"><span data-stu-id="da325-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="da325-109">Bu, bildirimi, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da325-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="da325-110">Örneğin, istenen "highestAvailable" veya "requireAdministrator" yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="da325-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da325-111">Bu seçenek ve [-win32res (C# derleyici seçenekleri)](./win32res-compiler-option.md) seçeneği birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="da325-111">This option and the [-win32res (C# Compiler Options)](./win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="da325-112">Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="da325-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="da325-113">İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir.</span><span class="sxs-lookup"><span data-stu-id="da325-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="da325-114">Daha fazla bilgi için bkz. [Kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="da325-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="da325-115">Uygulamanız, bu koşullardan biri doğru olduğunda sanallaştırmaya tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="da325-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
- <span data-ttu-id="da325-116">**-Nowin32manifest** seçeneğini kullanın ve **-win32res** seçeneğini kullanarak sonraki bir derleme adımında veya Windows kaynak (. res) dosyasının bir parçası olarak bir bildirim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="da325-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
- <span data-ttu-id="da325-117">İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="da325-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="da325-118">Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar.</span><span class="sxs-lookup"><span data-stu-id="da325-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="da325-119">Herhangi bir metin düzenleyicisinde bir tane oluşturarak ve sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da325-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="da325-120">Alternatif olarak, **Çözüm Gezgini**' de **Proje** simgesine sağ tıklayıp **Yeni öğe Ekle**' ye ve ardından **uygulama bildirim dosyası**' na tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da325-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="da325-121">Yeni veya mevcut bildirim dosyanızı ekledikten sonra, **bildirim** açılan listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="da325-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="da325-122">Daha fazla bilgi için bkz. [uygulama sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="da325-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="da325-123">Uygulama bildirimini özel derleme sonrası bir adım olarak veya bir Win32 kaynak dosyasının parçası olarak [-nowin32manifest (C# derleyici seçenekleri)](./nowin32manifest-compiler-option.md) seçeneğini kullanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da325-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](./nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="da325-124">Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="da325-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="da325-125">Bu, derleyicinin Taşınabilir çalıştırılabilir (PE) dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="da325-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da325-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="da325-126">Example</span></span>  
 <span data-ttu-id="da325-127">Aşağıdaki örnek, Visual C# DERLEYICISININ bir PE 'ye eklediği varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="da325-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da325-128">Derleyici, XML 'e "MyApplication. app" standart bir uygulama adı ekler.</span><span class="sxs-lookup"><span data-stu-id="da325-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="da325-129">Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="da325-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da325-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da325-130">See also</span></span>

- [<span data-ttu-id="da325-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="da325-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="da325-132">-nowin32manifest (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="da325-132">-nowin32manifest (C# Compiler Options)</span></span>](./nowin32manifest-compiler-option.md)
- [<span data-ttu-id="da325-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="da325-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
