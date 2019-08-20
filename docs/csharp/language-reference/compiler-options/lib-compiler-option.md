---
title: -lib (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606825"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="3b8b8-102">-lib (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3b8b8-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="3b8b8-103">**-Lib** seçeneği, [-Reference (C# derleyici seçenekleri)](./reference-compiler-option.md) seçeneği aracılığıyla başvurulan derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b8b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b8b8-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b8b8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3b8b8-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="3b8b8-106">Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde derleyicinin aranacağı bir dizin.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="3b8b8-107">Derleme başvuruları için arama yapılacak bir veya daha fazla dizin.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="3b8b8-108">Ek dizin adlarını virgülle ayırın ve aralarında boşluk olmadan boşluklar koyun.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b8b8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b8b8-109">Remarks</span></span>  
 <span data-ttu-id="3b8b8-110">Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:</span><span class="sxs-lookup"><span data-stu-id="3b8b8-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="3b8b8-111">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-111">Current working directory.</span></span> <span data-ttu-id="3b8b8-112">Bu, derleyicinin çağrıldığı dizindir.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="3b8b8-113">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="3b8b8-114">**-Lib**tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="3b8b8-115">LıB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="3b8b8-116">Derleme başvurusunu belirtmek için **-Reference** kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="3b8b8-117">**-lib** eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="3b8b8-118">**-Lib** kullanmanın bir alternatifi, gereken tüm derlemeleri çalışma dizinine kopyalamaktır; Bu, yalnızca derleme adını **başvuruya**iletmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="3b8b8-119">Daha sonra çalışma dizininden derlemeleri silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="3b8b8-120">Bağımlı derlemenin yolu bütünleştirilmiş kod bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve derlemeyi genel derleme önbelleğinde bulabilir ve kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="3b8b8-121">Derleyici derlemeye başvuru yapabildiğinden, ortak dil çalışma zamanının derlemeyi çalışma zamanında bulabileceği ve yükleyebilecektir anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="3b8b8-122">Çalışma zamanının başvurulmuş derlemeleri nasıl arayacağını görmek için bkz. [çalışma zamanının derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) .</span><span class="sxs-lookup"><span data-stu-id="3b8b8-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b8b8-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3b8b8-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3b8b8-124">Projenin **Özellik sayfaları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="3b8b8-125">**Başvurular yolu** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="3b8b8-126">Liste kutusunun içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="3b8b8-127">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b8b8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b8b8-128">Example</span></span>  
 <span data-ttu-id="3b8b8-129">Bir. exe dosyası oluşturmak için t2.cs derleyin.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="3b8b8-130">Derleyici, çalışma dizinine ve derleme başvuruları için C sürücüsünün kök dizinine bakacaktır.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b8b8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b8b8-131">See also</span></span>

- [<span data-ttu-id="3b8b8-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3b8b8-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3b8b8-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="3b8b8-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
