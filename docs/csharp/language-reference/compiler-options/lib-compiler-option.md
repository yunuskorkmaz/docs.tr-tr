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
ms.openlocfilehash: 49920a46f1d970c3f00025c3dc3eb384c937aa99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319410"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="6e34d-102">-lib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6e34d-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="6e34d-103">**-Lib** seçeneği tarafından başvurulan derlemelerin konumunu belirten [-başvurusu (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6e34d-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e34d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e34d-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e34d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e34d-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="6e34d-106">Geçerli çalışma dizinine sahipse Bakılacak başvurulan derlemenin derleme için bir dizin bulunamadı (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="6e34d-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="6e34d-107">Derleme başvuruları için aranacak bir veya daha fazla ek dizinler.</span><span class="sxs-lookup"><span data-stu-id="6e34d-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="6e34d-108">Ek dizin adları bunlar arasında boşluk olmadan ve virgül ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="6e34d-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e34d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e34d-109">Remarks</span></span>  
 <span data-ttu-id="6e34d-110">Derleyici şu sıralamadaki tam olmayan bütünleştirilmiş kod başvuruları arar:</span><span class="sxs-lookup"><span data-stu-id="6e34d-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="6e34d-111">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="6e34d-111">Current working directory.</span></span> <span data-ttu-id="6e34d-112">Bu, derleyicinin çağırıldığı dizinidir.</span><span class="sxs-lookup"><span data-stu-id="6e34d-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="6e34d-113">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="6e34d-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="6e34d-114">Tarafından belirtilen dizinlerde **-lib**.</span><span class="sxs-lookup"><span data-stu-id="6e34d-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="6e34d-115">LIB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="6e34d-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="6e34d-116">Kullanım **-başvuru** bir bütünleştirilmiş kod başvurusu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6e34d-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="6e34d-117">**-lib** eklenebilir; belirten olduğundan, birden çok kez önceki tüm değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="6e34d-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="6e34d-118">Kullanmaya alternatif **-lib** kopyalamaktır derlemeler çalışma dizinine gerekli; Bu, derleme adı için yalnızca geçmesine olanak tanır **-başvuru**.</span><span class="sxs-lookup"><span data-stu-id="6e34d-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="6e34d-119">Derlemeleri, ardından çalışma dizininden silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e34d-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="6e34d-120">Derleme bildiriminde bağımlı derleme yolu belirtilmediğinden, uygulamanın hedef bilgisayarda yeniden başlatılabilir ve bulup derleme genel derleme önbelleğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e34d-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="6e34d-121">Derleyici, derleme başvurusu çünkü ortak dil çalışma zamanı bulabilir ve derleme zamanında yükleme göstermez.</span><span class="sxs-lookup"><span data-stu-id="6e34d-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="6e34d-122">Bkz: [çalışma zamanı derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) nasıl başvurulan derlemeler için çalışma zamanı arama ile ilgili ayrıntılar.</span><span class="sxs-lookup"><span data-stu-id="6e34d-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6e34d-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6e34d-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6e34d-124">Projenin açın **özellik sayfaları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6e34d-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="6e34d-125">Tıklayın **başvuru yolu** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="6e34d-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="6e34d-126">Liste kutusunun içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6e34d-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="6e34d-127">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e34d-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e34d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e34d-128">Example</span></span>  
 <span data-ttu-id="6e34d-129">Bir .exe dosyası oluşturmak için T2.cs projesini derleyin.</span><span class="sxs-lookup"><span data-stu-id="6e34d-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="6e34d-130">Derleyici, derleme başvuruları için çalışma dizinini ve C sürücüsünün kök dizinindeki görünecektir.</span><span class="sxs-lookup"><span data-stu-id="6e34d-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e34d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e34d-131">See also</span></span>

- [<span data-ttu-id="6e34d-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e34d-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="6e34d-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6e34d-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
