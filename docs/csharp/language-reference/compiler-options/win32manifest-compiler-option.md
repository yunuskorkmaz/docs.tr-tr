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
ms.openlocfilehash: 9718febfe5aefba75decc133ad2113b64e4547de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618097"
---
# <a name="-win32manifest-c-compiler-options"></a><span data-ttu-id="9d29c-102">-win32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9d29c-102">-win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="9d29c-103">Kullanım **-win32manifest** projenin taşınabilir yürütülebilir (PE) dosya gömülü olması için bir kullanıcı tanımlı uygulama soubor manifestu Win32 için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d29c-103">Use the **-win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d29c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d29c-104">Syntax</span></span>  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d29c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d29c-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9d29c-106">Özel bildirim dosyasının konumunu ve adını.</span><span class="sxs-lookup"><span data-stu-id="9d29c-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d29c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d29c-107">Remarks</span></span>  
 <span data-ttu-id="9d29c-108">Varsayılan olarak, Visual C# derleyicisi "asInvoker" istenen yürütme düzeyini belirten bir uygulama bildirimi katıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d29c-108">By default, the Visual C# compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="9d29c-109">Bildirim, yürütülebilir dosya oluşturulduğuna göre genellikle bin\Debug veya bin\Release klasörü, Visual Studio kullandığınızda aynı klasörde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d29c-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="9d29c-110">Örneğin "highestAvailable" veya "requireAdministrator" istenen yürütme düzeyini belirtmek özel bir bildirim sağlamak istiyorsanız, dosya adını belirtmek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d29c-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d29c-111">Bu seçenek ve [-win32res (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) seçeneği karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="9d29c-111">This option and the [-win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="9d29c-112">Aynı komut satırında iki seçenek de kullanmayı denerseniz bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9d29c-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="9d29c-113">Hiçbir uygulama bildirimini olan bir uygulama, istenen yürütme düzeyini dosya/kayıt defteri sanallaştırma Windows kullanıcı hesabı denetimi özelliği altında tabi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d29c-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows.</span></span> <span data-ttu-id="9d29c-114">Daha fazla bilgi için [kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).</span><span class="sxs-lookup"><span data-stu-id="9d29c-114">For more information, see [User Account Control](/windows/access-protection/user-account-control/user-account-control-overview).</span></span>  
  
 <span data-ttu-id="9d29c-115">Bu koşullardan biri doğru ise, uygulama sanallaştırma tabi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="9d29c-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="9d29c-116">Kullandığınız **-nowin32manifest** seçeneğini sağlamaz daha yeni bir derleme adımı veya bir Windows kaynağı (.res) dosyasının bir parçası olarak bir bildirim kullanarak **-win32res** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d29c-116">You use the **-nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **-win32res** option.</span></span>  
  
-   <span data-ttu-id="9d29c-117">İstenen yürütme düzeyini belirtmeyen bir özel bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d29c-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="9d29c-118">Visual Studio varsayılan .manifest dosyasını oluşturur ve hata ayıklama ve yayın dizinleri yürütülebilir dosyanın yanında depolar.</span><span class="sxs-lookup"><span data-stu-id="9d29c-118">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="9d29c-119">Herhangi bir metin düzenleyicisinde oluşturma ve sonra dosyayı projeye ekleyerek, özel bir bildirim ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d29c-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="9d29c-120">Alternatif olarak, sağ **proje** simgesini **Çözüm Gezgini**, tıklayın **Yeni Öğe Ekle**ve ardından **uygulama bildirim dosyası**.</span><span class="sxs-lookup"><span data-stu-id="9d29c-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="9d29c-121">Yeni veya var olan bildirim dosyası ekledikten sonra görüneceği **bildirim** açılan liste.</span><span class="sxs-lookup"><span data-stu-id="9d29c-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="9d29c-122">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="9d29c-122">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="9d29c-123">Kullanarak bir Win32 kaynak dosyası bir parçası olarak veya özel bir derleme sonrası adımı olarak uygulama bildirimine sağlayabilirsiniz [-nowin32manifest (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d29c-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [-nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="9d29c-124">Uygulamanızın Windows Vista dosya veya kayıt defteri sanallaştırma tabi olmasını istiyorsanız, aynı bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d29c-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="9d29c-125">Bu, derleyicinin oluşturmasını ve taşınabilir yürütülebilir (PE) dosyasında bir varsayılan bildirim gömülüyor engeller.</span><span class="sxs-lookup"><span data-stu-id="9d29c-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d29c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d29c-126">Example</span></span>  
 <span data-ttu-id="9d29c-127">Aşağıdaki örnek, Visual C# derleyicisinin bir PE ekler, varsayılan bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d29c-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d29c-128">Derleyicinin, xml verilerinin standart uygulama adı "MyApplication.app şeklinde" ekler.</span><span class="sxs-lookup"><span data-stu-id="9d29c-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="9d29c-129">Windows Server 2003 Service Pack 3'üzerinde çalıştırılacak uygulamaları etkinleştirmek için geçici bir çözüm budur.</span><span class="sxs-lookup"><span data-stu-id="9d29c-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d29c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d29c-130">See also</span></span>

- [<span data-ttu-id="9d29c-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9d29c-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="9d29c-132">-nowin32manifest (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9d29c-132">-nowin32manifest (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)
- [<span data-ttu-id="9d29c-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="9d29c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
