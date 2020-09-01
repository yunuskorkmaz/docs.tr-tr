---
description: -Main (C# derleyici seçenekleri)
title: -Main (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 61e63de8082a335b448ffee1ae35170d3a1cf6b4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125273"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="191c6-103">-Main (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="191c6-103">-main (C# Compiler Options)</span></span>

<span data-ttu-id="191c6-104">Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="191c6-104">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>

## <a name="syntax"></a><span data-ttu-id="191c6-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="191c6-105">Syntax</span></span>

```console
-main:class
```

## <a name="arguments"></a><span data-ttu-id="191c6-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="191c6-106">Arguments</span></span>
 `class`  
 <span data-ttu-id="191c6-107">**Main** metodunu içeren tür.</span><span class="sxs-lookup"><span data-stu-id="191c6-107">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="191c6-108">Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="191c6-108">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="191c6-109">Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` .</span><span class="sxs-lookup"><span data-stu-id="191c6-109">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>

## <a name="remarks"></a><span data-ttu-id="191c6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="191c6-110">Remarks</span></span>

<span data-ttu-id="191c6-111">Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="191c6-111">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>

<span data-ttu-id="191c6-112">Bu seçenek bir *. exe* dosyası derlenirken kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="191c6-112">This option is for use when compiling an *.exe* file.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="191c6-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="191c6-113">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="191c6-114">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="191c6-114">Open the project's **Properties** page.</span></span>

2. <span data-ttu-id="191c6-115">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="191c6-115">Click the **Application** property page.</span></span>

3. <span data-ttu-id="191c6-116">**Başlangıç nesnesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="191c6-116">Modify the **Startup object** property.</span></span>

    <span data-ttu-id="191c6-117">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> ..</span><span class="sxs-lookup"><span data-stu-id="191c6-117">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="191c6-118">Bu derleyici seçeneğini *. csproj* dosyasını el ile düzenleyerek ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="191c6-118">To set this compiler option by manually editing the *.csproj* file</span></span>

<span data-ttu-id="191c6-119">Bu seçeneği,. csproj dosyasını düzenleyerek ve bölümünün içine bir öğe ekleyerek ayarlayabilirsiniz `StartupObject` `PropertyGroup` .</span><span class="sxs-lookup"><span data-stu-id="191c6-119">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="191c6-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="191c6-120">For example:</span></span>

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="191c6-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="191c6-121">Example</span></span>

<span data-ttu-id="191c6-122">`t2.cs`Ve `t3.cs` ' de **Main** yönteminin bulunduğunu belirterek derleyin `Test2` :</span><span class="sxs-lookup"><span data-stu-id="191c6-122">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a><span data-ttu-id="191c6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191c6-123">See also</span></span>

- [<span data-ttu-id="191c6-124">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="191c6-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="191c6-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="191c6-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
