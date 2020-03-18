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
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606825"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="3b518-102">-lib (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3b518-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="3b518-103">**-lib** seçeneği, [-referans (C# Derleyici Seçenekleri)](./reference-compiler-option.md) seçeneği ile başvurulan derlemelerin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b518-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b518-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b518-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b518-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3b518-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="3b518-106">Başvurulan derlemenin geçerli çalışma dizininde (derleyiciyi çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanı sistem dizininde bulunamazsa bakması için derleyicinin dizini.</span><span class="sxs-lookup"><span data-stu-id="3b518-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="3b518-107">Derleme başvurularında aranacak bir veya daha fazla ek dizin.</span><span class="sxs-lookup"><span data-stu-id="3b518-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="3b518-108">Virgülle ve aralarında beyaz boşluk olmayan ek dizin adlarını ayırın.</span><span class="sxs-lookup"><span data-stu-id="3b518-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b518-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b518-109">Remarks</span></span>  
 <span data-ttu-id="3b518-110">Derleyici, aşağıdaki sırada tam olarak nitelikli olmayan derleme başvurularını arar:</span><span class="sxs-lookup"><span data-stu-id="3b518-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="3b518-111">Geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="3b518-111">Current working directory.</span></span> <span data-ttu-id="3b518-112">Bu, derleyicinin çağrıldığı dizindir.</span><span class="sxs-lookup"><span data-stu-id="3b518-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="3b518-113">Ortak dil çalışma zamanı sistem dizini.</span><span class="sxs-lookup"><span data-stu-id="3b518-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="3b518-114">**-lib**tarafından belirtilen dizinler .</span><span class="sxs-lookup"><span data-stu-id="3b518-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="3b518-115">LIB ortam değişkeni tarafından belirtilen dizinler.</span><span class="sxs-lookup"><span data-stu-id="3b518-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="3b518-116">Bir derleme başvurusu belirtmek için **-başvuru** kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b518-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="3b518-117">**-lib** katkı maddesidir; önceki değerlere bir kereden fazla ekleyen.</span><span class="sxs-lookup"><span data-stu-id="3b518-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="3b518-118">**-lib'i** kullanmaya alternatif olarak, gerekli derlemeleri çalışma dizinine kopyalamak; bu sadece **-referans**için derleme adını geçmek için izin verecektir.</span><span class="sxs-lookup"><span data-stu-id="3b518-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="3b518-119">Daha sonra derlemeleri çalışma dizininden silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b518-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="3b518-120">Bağımlı derlemeye giden yol derleme bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve derlemeyi genel derleme önbelleğinde bulur ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b518-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="3b518-121">Derleyici derlemebaşvuru olabilir çünkü ortak dil çalışma süresi bulmak ve çalışma zamanında derleme yüklemek mümkün olacağı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="3b518-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="3b518-122">Çalışma zamanının başvurulan derlemeleri nasıl aradığına ilişkin ayrıntılar için [Çalışma Zamanı Derlemelerini Nasıl Bulur'a](../../../framework/deployment/how-the-runtime-locates-assemblies.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="3b518-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3b518-123">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3b518-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3b518-124">Projenin **Özellik Sayfaları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="3b518-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="3b518-125">Başvurular **Yolu** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3b518-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="3b518-126">Liste kutusunun içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3b518-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="3b518-127">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A></span><span class="sxs-lookup"><span data-stu-id="3b518-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b518-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b518-128">Example</span></span>  
 <span data-ttu-id="3b518-129">Bir .exe dosyası oluşturmak için t2.cs derle.</span><span class="sxs-lookup"><span data-stu-id="3b518-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="3b518-130">Derleyici çalışma dizinine ve derleme başvuruları için C sürücüsünün kök dizinine bakar.</span><span class="sxs-lookup"><span data-stu-id="3b518-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b518-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b518-131">See also</span></span>

- [<span data-ttu-id="3b518-132">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3b518-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3b518-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="3b518-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
