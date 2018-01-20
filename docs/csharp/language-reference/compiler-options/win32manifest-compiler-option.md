---
title: "-win32manifest (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36a16f1ee037a1379399c7ee2e2c67427eb9d1b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="ef450-102">-win32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ef450-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="ef450-103">Kullanım **-win32manifest** seçeneği bir projenin taşınabilir yürütülebilir (PE) dosyasına katıştırılmış bir kullanıcı tarafından tanımlanan Win32 uygulama bildirim dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="ef450-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef450-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef450-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef450-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ef450-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="ef450-106">Özel bildirim dosyasının konumunu ve adını.</span><span class="sxs-lookup"><span data-stu-id="ef450-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef450-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef450-107">Remarks</span></span>  
 <span data-ttu-id="ef450-108">Varsayılan olarak, [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] derleyici katıştırır "asInvoker." istenen yürütme düzeyini belirten bir uygulama bildirimi</span><span class="sxs-lookup"><span data-stu-id="ef450-108">By default, the [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="ef450-109">Hangi yürütülebilir yapılandırıldığında, genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef450-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="ef450-110">Örneğin "highestAvailable" veya "requireAdministrator" istenen yürütme düzeyini belirtmek özel bir bildirimi sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef450-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef450-111">Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) seçeneği karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="ef450-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="ef450-112">Her iki seçenek aynı komut satırında kullanmaya çalışırsa, bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ef450-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="ef450-113">Hiçbir uygulama bildirimini olan bir uygulama, istenen yürütme düzeyinin Windows kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırma tabi olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef450-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="ef450-114">Daha fazla bilgi için bkz: [kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="ef450-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="ef450-115">Bu koşulların doğru ise, uygulama sanallaştırma tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="ef450-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="ef450-116">Kullandığınız **-nowin32manifest** seçeneğini sağlamaz daha yeni bir derleme adımı veya Windows Kaynak (.res) dosyasının bir parçası olarak bir bildirim kullanarak **-win32res** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ef450-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="ef450-117">İstenen yürütme düzeyinin belirtmiyor özel bir bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef450-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="ef450-118">Varsayılan bir .manifest dosyası oluşturur ve yürütülebilir dosyanın yanında hata ayıklama ve yayın dizinleri depolar.</span><span class="sxs-lookup"><span data-stu-id="ef450-118"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="ef450-119">Özel bir bildirimi, aşağıdakilerden herhangi bir metin düzenleyicisinde oluşturarak ve ardından dosyayı projeye ekleyerek ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef450-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="ef450-120">Alternatif olarak, sağ tıklayarak **proje** simgesine **Çözüm Gezgini**, tıklatın **Yeni Öğe Ekle**ve ardından **uygulama bildirim dosyası**.</span><span class="sxs-lookup"><span data-stu-id="ef450-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="ef450-121">Yeni veya varolan bildirim dosyanızı ekledikten sonra görüneceği **bildirim** açılan liste.</span><span class="sxs-lookup"><span data-stu-id="ef450-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="ef450-122">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ef450-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="ef450-123">Kullanarak oluşturma sonrası özel bir adım veya Win32 kaynak dosyasını bir parçası olarak uygulama bildirimini sağlayabilirsiniz [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ef450-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="ef450-124">Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız aynı seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef450-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="ef450-125">Bu oluşturma ve taşınabilir yürütülebilir (PE) dosyasında varsayılan bildirim katıştırma derleyici engeller.</span><span class="sxs-lookup"><span data-stu-id="ef450-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef450-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef450-126">Example</span></span>  
 <span data-ttu-id="ef450-127">Aşağıdaki örnek, Visual C# Derleyici bir PE'ye eklediği varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef450-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef450-128">Derleyici standart uygulama adı "MyApplication.app şeklinde" xml öğesine ekler.</span><span class="sxs-lookup"><span data-stu-id="ef450-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="ef450-129">Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını etkinleştirmek için bir çözüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef450-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef450-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef450-130">See Also</span></span>  
 [<span data-ttu-id="ef450-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ef450-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ef450-132">-nowin32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ef450-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [<span data-ttu-id="ef450-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ef450-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
