---
title: -Main (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 7d3cfce474023907eda0bc40b692e4bbb65ffb96
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802840"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="49915-102">-Main (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="49915-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="49915-103">Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="49915-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49915-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="49915-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="49915-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="49915-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="49915-106">**Main** metodunu içeren tür.</span><span class="sxs-lookup"><span data-stu-id="49915-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="49915-107">Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="49915-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="49915-108">Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` .</span><span class="sxs-lookup"><span data-stu-id="49915-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="49915-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49915-109">Remarks</span></span>  
 <span data-ttu-id="49915-110">Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49915-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="49915-111">Bu seçenek bir. exe dosyası derlenirken kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="49915-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="49915-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="49915-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="49915-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="49915-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="49915-114">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="49915-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="49915-115">**Başlangıç nesnesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="49915-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="49915-116">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> ..</span><span class="sxs-lookup"><span data-stu-id="49915-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="49915-117">Bu derleyici seçeneğini. csproj dosyasını el ile düzenleyerek ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="49915-117">To set this compiler option by manually editing the .csproj file</span></span>
  
<span data-ttu-id="49915-118">Bu seçeneği,. csproj dosyasını düzenleyerek ve bölümünün içine bir öğe ekleyerek ayarlayabilirsiniz `StartupObject` `PropertyGroup` .</span><span class="sxs-lookup"><span data-stu-id="49915-118">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="49915-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="49915-119">For example:</span></span>

```
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="49915-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="49915-120">Example</span></span>  
 <span data-ttu-id="49915-121">`t2.cs`Ve `t3.cs` ' de **Main** yönteminin bulunduğunu belirterek derleyin `Test2` :</span><span class="sxs-lookup"><span data-stu-id="49915-121">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="49915-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49915-122">See also</span></span>

- [<span data-ttu-id="49915-123">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="49915-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="49915-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="49915-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
