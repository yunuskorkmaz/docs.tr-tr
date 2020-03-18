---
title: -win32manifest (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924682"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="e17b3-102">-win32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e17b3-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="e17b3-103">Bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılması için kullanıcı tanımlı Win32 uygulama bildirimi dosyasını belirtmek için **-win32manifest** seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e17b3-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e17b3-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e17b3-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e17b3-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e17b3-106">Özel bildirim dosyasının adı ve konumu.</span><span class="sxs-lookup"><span data-stu-id="e17b3-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e17b3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e17b3-107">Remarks</span></span>  
 <span data-ttu-id="e17b3-108">Varsayılan olarak, Visual C# derleyicisi istenen yürütme düzeyini belirten bir uygulama bildirimi "asInvoker" gömer.</span><span class="sxs-lookup"><span data-stu-id="e17b3-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="e17b3-109">Görsel Studio'yu kullandığınızda, genellikle bin\Debug veya bin\Release klasörü olan yürütülebilir yapılının bulunduğu klasörde manifesto oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e17b3-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="e17b3-110">Örneğin, "en yüksek Kullanılabilir" veya "zorunlu Yönetici" için istenen yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e17b3-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e17b3-111">Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](./win32res-compiler-option.md) seçeneği birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="e17b3-111">This option and the [-win32res (C# Compiler Options)](./win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="e17b3-112">Her iki seçeneği de aynı komut satırında kullanmaya çalışırsanız bir yapı hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e17b3-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="e17b3-113">İstenen yürütme düzeyini belirten bir uygulama bildirimi olmayan bir uygulama, Windows'daki Kullanıcı Hesabı Denetimi özelliği altında dosya/kayıt defteri sanallaştırmasına tabi tutulur.</span><span class="sxs-lookup"><span data-stu-id="e17b3-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="e17b3-114">Daha fazla bilgi için [Bkz. Kullanıcı Hesabı Denetimi.](/windows/access-protection/user-account-control/user-account-control-overview)</span><span class="sxs-lookup"><span data-stu-id="e17b3-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="e17b3-115">Bu koşullardan biri doğruysa, uygulamanız sanallaştırmaya tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="e17b3-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
- <span data-ttu-id="e17b3-116">**-nowin32manifest** seçeneğini kullanırsınız ve **-win32res** seçeneğini kullanarak daha sonraki bir yapı adımında veya Windows Resource (.res) dosyasının bir parçası olarak bir bildirim sağlamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e17b3-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
- <span data-ttu-id="e17b3-117">İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e17b3-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="e17b3-118">Visual Studio varsayılan bir .manifest dosyası oluşturur ve yürütülebilir dosyanın yanında hata ayıklama ve sürüm dizinlerinde saklar.</span><span class="sxs-lookup"><span data-stu-id="e17b3-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="e17b3-119">Herhangi bir metin düzenleyicisinde bir tane oluşturup sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e17b3-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="e17b3-120">Alternatif olarak, **Çözüm Gezgini'nde** **Proje** simgesine sağ tıklayabilir, **Yeni Öğe Ekle'yi**tıklatın ve ardından Uygulama Bildirimi **Dosyası'nı**tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e17b3-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="e17b3-121">Yeni veya varolan bildirim dosyanızı ekledikten sonra, bu dosya **Bildirim** açılır listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="e17b3-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="e17b3-122">Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="e17b3-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="e17b3-123">[-nowin32manifest (C# Derleyici Seçenekleri)](./nowin32manifest-compiler-option.md) seçeneğini kullanarak uygulama bildirimini özel bir post-build adımı olarak veya Win32 kaynak dosyasının bir parçası olarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e17b3-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](./nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="e17b3-124">Uygulamanızın Windows Vista'da dosya veya kayıt defteri sanallaştırmasına tabi olmasını istiyorsanız aynı seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e17b3-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="e17b3-125">Bu, derleyicinin taşınabilir çalıştırılabilir (PE) dosyasına varsayılan bir bildirim oluşturmasını ve katıştırmasını önler.</span><span class="sxs-lookup"><span data-stu-id="e17b3-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e17b3-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="e17b3-126">Example</span></span>  
 <span data-ttu-id="e17b3-127">Aşağıdaki örnek, Visual C# derleyicisinin PE'ye ekleyen varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e17b3-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e17b3-128">Derleyici xml'e standart bir uygulama adı " MyApplication.app " ekler.</span><span class="sxs-lookup"><span data-stu-id="e17b3-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="e17b3-129">Bu, uygulamaların Windows Server 2003 Hizmet Paketi 3'te çalışmasını sağlamak için geçici çözümdür.</span><span class="sxs-lookup"><span data-stu-id="e17b3-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e17b3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e17b3-130">See also</span></span>

- [<span data-ttu-id="e17b3-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e17b3-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e17b3-132">-nowin32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e17b3-132">-nowin32manifest (C# Compiler Options)</span></span>](./nowin32manifest-compiler-option.md)
- [<span data-ttu-id="e17b3-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e17b3-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
