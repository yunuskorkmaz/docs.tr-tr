---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 623df8aa86d25d9a57d3039bee01b0ee39d402a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123934"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="e9152-102">Nasıl yapılır: COM Sarmalayıcıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9152-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="e9152-103">Visual Studio 2005 özelliklerini veya .NET Framework araçları Tlbimp. exe ve Regasm. exe ' yi kullanarak bileşen nesne modeli (COM) sarmalayıcıları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="e9152-104">Her iki yöntem de iki tür COM sarmalayıcıları üretir:</span><span class="sxs-lookup"><span data-stu-id="e9152-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="e9152-105">Yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığından bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="e9152-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="e9152-106">Yerel bir uygulamada yönetilen bir nesne çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarmalayıcı](../../standard/native-interop/com-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="e9152-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="e9152-107">Visual Studio 2005 ' de COM sarmalayıcısı ' ı projenize bir başvuru olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="e9152-108">Yönetilen bir uygulamadaki COM nesnelerini sarın</span><span class="sxs-lookup"><span data-stu-id="e9152-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="e9152-109">Visual Studio kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9152-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="e9152-110">Yönetilen uygulamanız için projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="e9152-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="e9152-111">**Proje** menüsünde **tüm dosyaları göster**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="e9152-112">**Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="e9152-113">Başvuru Ekle iletişim kutusunda, **com** sekmesine tıklayın, kullanmak istediğiniz bileşeni seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="e9152-114">**Çözüm Gezgini**, com bileşeninin projenizdeki başvurular klasörüne eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="e9152-115">Artık COM nesnesine erişmek için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="e9152-116">Nesnesini bildirerek, Visual Basic için bir `Imports` ifadesiyle veya için C#bir `Using` bildirimiyle başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="e9152-117">Microsoft Office bileşenleri programlamak istiyorsanız, önce Microsoft Indirme merkezi 'nden [Microsoft Office birincil birlikte çalışma derlemelerini](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e9152-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="e9152-118">4\. adımda, **Microsoft Word 11,0 nesne kitaplığı**gibi istediğiniz Office ürünü için uygun nesne kitaplığının en son sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e9152-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="e9152-119">.NET Framework araçlarını kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9152-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="e9152-120">[Tlbimp. exe (tür kitaplığı Içeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9152-120">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="e9152-121">Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verilerini içeren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9152-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="e9152-122">Yönetilen nesneleri yerel bir uygulamada sarın</span><span class="sxs-lookup"><span data-stu-id="e9152-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="e9152-123">Visual Studio kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9152-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="e9152-124">Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e9152-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="e9152-125">Sınıf parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9152-125">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="e9152-126">AssemblyInfo dosyasında derlemelerinizin dört bölümden oluşan tam bir sürüm numarasına sahip olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="e9152-127">Bu sayı, Windows kayıt defterinde sürüm oluşturmayı sürdürmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e9152-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="e9152-128">Sürüm numaraları hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="e9152-128">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="e9152-129">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-129">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="e9152-130">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e9152-130">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="e9152-131">**Com birlikte çalışması Için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e9152-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="e9152-132">Projeyi derlediğinizde, derleme otomatik olarak COM birlikte çalışma için kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e9152-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="e9152-133">Visual Studio 2005 ' de yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayarak derlemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="e9152-134">.NET Framework araçlarını kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e9152-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="e9152-135">[Regasm. exe (derleme kayıt aracı)](../tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9152-135">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="e9152-136">Bu araç derleme meta verilerini okur ve gerekli girdileri kayıt defterine ekler.</span><span class="sxs-lookup"><span data-stu-id="e9152-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="e9152-137">Sonuç olarak, COM istemcileri .NET Framework sınıfları saydam şekilde oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e9152-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="e9152-138">Derlemeyi yerel bir COM sınıfı gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="e9152-139">Herhangi bir dizinde bulunan bir derlemede Regasm. exe ' yi çalıştırabilir ve ardından [Gacutil. exe ' yi (genel bütünleştirilmiş kod önbelleği aracı)](../tools/gacutil-exe-gac-tool.md) çalıştırarak genel derleme önbelleğine taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9152-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="e9152-140">Derlemenin taşınması konum kayıt defteri girdilerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.</span><span class="sxs-lookup"><span data-stu-id="e9152-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9152-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9152-141">See also</span></span>

- [<span data-ttu-id="e9152-142">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="e9152-142">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="e9152-143">COM Çağrılabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="e9152-143">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
