---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c26c84ece1231a4e118144c163fa3e9c7619301
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324141"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="fffc0-102">Nasıl yapılır: COM Sarmalayıcıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fffc0-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="fffc0-103">Bileşen Nesne Modeli (COM) sarmalayıcılar Visual Studio 2005 özellikleri veya .NET Framework Araçları, Tlbimp.exe ve RegAsm.exe'yi kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="fffc0-104">Her iki yöntem de iki tür COM sarmalayıcıları oluşturma:</span><span class="sxs-lookup"><span data-stu-id="fffc0-104">Both methods generate two types of COM wrappers:</span></span>

-   <span data-ttu-id="fffc0-105">A [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) COM nesnesinin yönetilen kodu çalıştırmak için bir tür kitaplığından.</span><span class="sxs-lookup"><span data-stu-id="fffc0-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

-   <span data-ttu-id="fffc0-106">A [COM çağrılabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) ile yönetilen bir nesneye yerel bir uygulamada çalıştırmak için gerekli kayıt defteri ayarları.</span><span class="sxs-lookup"><span data-stu-id="fffc0-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="fffc0-107">Visual Studio 2005'te, projenize bir başvuru olarak COM sarmalayıcı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="fffc0-108">Yönetilen bir uygulamada COM nesneleri Kaydır</span><span class="sxs-lookup"><span data-stu-id="fffc0-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="fffc0-109">Visual Studio kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fffc0-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="fffc0-110">Yönetilen uygulamanız için projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="fffc0-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="fffc0-111">Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="fffc0-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="fffc0-112">Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="fffc0-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="fffc0-113">Başvuru Ekle iletişim kutusuna tıklayın **COM** sekmesinde, seçmek istediğiniz tıklatın ve bileşeni **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="fffc0-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="fffc0-114">İçinde **Çözüm Gezgini**, projenizi başvurular klasörüne COM bileşeninin eklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fffc0-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="fffc0-115">Artık, COM nesnesi erişmek için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="fffc0-116">Nesne gibi ile bildirerek başlayın bir `Imports` bildirimi [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] veya `Using` bildirimi [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fffc0-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="fffc0-117">Program için Microsoft Office bileşenleri istiyorsanız, önce yükleme [Microsoft Office birincil birlikte çalışma derlemeleri](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) gelen Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="fffc0-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="fffc0-118">4. adımda Nesne Kitaplığı gibi yüklemek istediğiniz Office ürün için kullanılabilen en son sürümünü seçin **Microsoft Word 11.0 Nesne Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="fffc0-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="fffc0-119">.NET Framework Araçları'nı kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fffc0-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="fffc0-120">Çalıştırma [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="fffc0-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="fffc0-121">Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verileri içeren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fffc0-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="fffc0-122">Yerel bir uygulamada yönetilen nesneleri saran</span><span class="sxs-lookup"><span data-stu-id="fffc0-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="fffc0-123">Visual Studio kullanarak COM çağrılabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fffc0-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="fffc0-124">Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fffc0-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="fffc0-125">Sınıfı, bir varsayılan oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fffc0-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="fffc0-126">AssemblyInfo dosyası içinde derleme için bir tam Dört bölümlü sürüm numarasına sahip olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fffc0-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="fffc0-127">Bu sayı, sürüm oluşturma Windows kayıt defterinde bakımı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fffc0-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="fffc0-128">Sürüm numaraları hakkında daha fazla bilgi için bkz: [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="fffc0-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2. <span data-ttu-id="fffc0-129">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="fffc0-129">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="fffc0-130">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="fffc0-130">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="fffc0-131">Seçin **kaydetme COM birlikte çalışması için** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="fffc0-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="fffc0-132">Proje oluşturduğunuzda, derlemenin COM birlikte çalışması için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fffc0-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="fffc0-133">Visual Studio 2005 yerel bir uygulama oluşturuyorsanız tıklayarak derleme kullanabilirsiniz **Başvuru Ekle** üzerinde **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="fffc0-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="fffc0-134">.NET Framework araçları kullanarak COM çağrılabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fffc0-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="fffc0-135">Çalıştırma [Regasm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="fffc0-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="fffc0-136">Bu araç, derleme meta verileri okur ve kayıt defterine gerekli girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="fffc0-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="fffc0-137">Sonuç olarak, COM istemcilerinin şeffaf bir şekilde .NET Framework sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="fffc0-138">Yerel bir COM sınıfı gibi derleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="fffc0-139">Herhangi bir dizinde bulunan bir derlemeyi Regasm.exe çalıştırın ve ardından çalıştırın [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel bütünleştirilmiş kod önbelleğine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="fffc0-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="fffc0-140">Derleme başka bir yerde bulunamazsa genel derleme önbelleği her zaman incelenir çünkü derleme taşıma konumu, kayıt defteri girdilerini geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffc0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fffc0-141">See also</span></span>

- [<span data-ttu-id="fffc0-142">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="fffc0-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="fffc0-143">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="fffc0-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
