---
title: -lib (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 7db975909f498a0b84e7405a12a8f8ec1e2dd34b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216862"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="23c62-102">-lib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="23c62-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="23c62-103">**-Lib** seçeneği tarafından başvurulan derlemelerin konumunu belirleyen [-başvurusu (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="23c62-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23c62-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="23c62-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="23c62-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="23c62-106">Başvurulan bir derleme IF Bakılacak derleme için bir dizin geçerli çalışma dizininde bulunamadı (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanı 's sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="23c62-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="23c62-107">Derleme başvuruları için aranacak bir veya daha fazla ek dizinler.</span><span class="sxs-lookup"><span data-stu-id="23c62-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="23c62-108">Ek dizin adlarını virgül ve boşluk aralarında olmadan ayırın.</span><span class="sxs-lookup"><span data-stu-id="23c62-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23c62-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23c62-109">Remarks</span></span>  
 <span data-ttu-id="23c62-110">Aşağıdaki sırayla tam olarak nitelenmiş değil derleme başvurularını derleyici arar:</span><span class="sxs-lookup"><span data-stu-id="23c62-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="23c62-111">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="23c62-111">Current working directory.</span></span> <span data-ttu-id="23c62-112">Bu, derleyicinin çağırıldığı dizindir.</span><span class="sxs-lookup"><span data-stu-id="23c62-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="23c62-113">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="23c62-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="23c62-114">Tarafından belirtilen dizin **-lib**.</span><span class="sxs-lookup"><span data-stu-id="23c62-114">Directories specified by **-lib**.</span></span>  
  
4.  <span data-ttu-id="23c62-115">LIB ortam değişkeni tarafından belirtilen dizin.</span><span class="sxs-lookup"><span data-stu-id="23c62-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="23c62-116">Kullanım **-başvuru** bir derleme başvurusu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="23c62-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="23c62-117">**-lib** şu eklenebilir; belirten daha çok kez herhangi bir önceki değeri ekler.</span><span class="sxs-lookup"><span data-stu-id="23c62-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="23c62-118">Kullanmaya alternatif **-lib** kopyalamaktır çalışma dizinine derlemeleri gerekli; Bu, derleme adı geçmesine izin verir **-başvuru**.</span><span class="sxs-lookup"><span data-stu-id="23c62-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="23c62-119">Derlemeleri çalışma dizininden sonra silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23c62-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="23c62-120">Bağımlı derleme yolu derleme bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve bulmak ve genel derleme önbelleğinde derleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="23c62-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="23c62-121">Derleyici derleme başvurusu yapabilir nedeniyle ortak dil çalışma zamanı bulmak ve derleme zamanında yükleyemediğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="23c62-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="23c62-122">Bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../framework/deployment/how-the-runtime-locates-assemblies.md) nasıl başvurulan derlemeler için çalışma zamanı arama ile ilgili ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="23c62-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="23c62-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="23c62-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="23c62-124">Projenin açmak **özellik sayfaları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="23c62-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="23c62-125">Tıklatın **başvuruları yolu** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="23c62-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="23c62-126">Liste kutusu içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="23c62-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="23c62-127">Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="23c62-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23c62-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="23c62-128">Example</span></span>  
 <span data-ttu-id="23c62-129">Bir .exe dosyası oluşturmak için T2.cs projesini derleyin.</span><span class="sxs-lookup"><span data-stu-id="23c62-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="23c62-130">Derleyici derleme başvuruları için çalışma dizini ve C sürücüsünün kök dizininde arar.</span><span class="sxs-lookup"><span data-stu-id="23c62-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="23c62-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23c62-131">See Also</span></span>  
 [<span data-ttu-id="23c62-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="23c62-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="23c62-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="23c62-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
