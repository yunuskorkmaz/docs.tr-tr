---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4deb355a7b523437ae31a1d2b9c79e3b8d4f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="eec13-102">Nasıl yapılır: COM Sarmalayıcıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eec13-102">How to: Create COM Wrappers</span></span>
<span data-ttu-id="eec13-103">Bileşen Nesne Modeli (COM) sarmalayıcıları kullanarak oluşturabileceğiniz [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] özellikleri veya .NET Framework Araçları Tlbimp.exe ve Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="eec13-103">You can create Component Object Model (COM) wrappers by using [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="eec13-104">Her iki yöntem de iki tür COM sarmalayıcıları oluştur:</span><span class="sxs-lookup"><span data-stu-id="eec13-104">Both methods generate two types of COM wrappers:</span></span>  
  
-   <span data-ttu-id="eec13-105">A [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="eec13-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>  
  
-   <span data-ttu-id="eec13-106">A [COM aranabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) yönetilen bir nesnenin bir yerel uygulamayı çalıştırmak için gerekli kayıt defteri ayarları.</span><span class="sxs-lookup"><span data-stu-id="eec13-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>  
  
 <span data-ttu-id="eec13-107">İçinde [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], projenizin bir başvuru olarak COM sarmalayıcı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec13-107">In [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can add the COM wrapper as a reference to your project.</span></span>  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a><span data-ttu-id="eec13-108">Yönetilen bir uygulamada COM nesneleri kaydırma</span><span class="sxs-lookup"><span data-stu-id="eec13-108">Wrapping COM Objects in a Managed Application</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="eec13-109">Visual Studio kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eec13-109">To create a runtime callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="eec13-110">Yönetilen uygulamanızın projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="eec13-110">Open the project for your managed application.</span></span>  
  
2.  <span data-ttu-id="eec13-111">Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="eec13-111">On the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="eec13-112">Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="eec13-112">On the **Project** menu, click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="eec13-113">Başvuru Ekle iletişim kutusunda tıklatın **COM** sekmesinde, kullanın ve istediğiniz bileşeni seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="eec13-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>  
  
     <span data-ttu-id="eec13-114">İçinde **Çözüm Gezgini**, COM bileşeni projenize başvuruları klasöre eklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="eec13-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>  
  
 <span data-ttu-id="eec13-115">Şimdi COM nesnesi erişmek için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec13-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="eec13-116">Nesne gibi ile bildirerek başlamak için bir `Imports` deyimi için [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] veya `Using` bildirimi [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eec13-116">You can begin by declaring the object, such as with an `Imports` statement for [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] or a `Using` statement for [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eec13-117">Program Microsoft Office bileşenleri istiyorsanız, önce yükleme [Microsoft Office birincil birlikte çalışma derlemeleri](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA) Microsoft Download Center gelen.</span><span class="sxs-lookup"><span data-stu-id="eec13-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="eec13-118">4. adımda Nesne Kitaplığı istediğiniz gibi Office ürün için kullanılabilir en son sürümünü seçin **Microsoft Word 11.0 Nesne Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="eec13-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="eec13-119">.NET Framework Araçları'nı kullanarak bir çalışma zamanı aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eec13-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="eec13-120">Çalıştırma [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="eec13-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="eec13-121">Bu araç, özgün Tür Kitaplığı'nda tanımlanan türler için çalışma zamanı meta verileri içeren bütünleştirilmiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eec13-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a><span data-ttu-id="eec13-122">Yerel uygulama nesnelerinin kaydırma yönetilen</span><span class="sxs-lookup"><span data-stu-id="eec13-122">Wrapping Managed Objects in a Native Application</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="eec13-123">Visual Studio kullanarak bir COM aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eec13-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1.  <span data-ttu-id="eec13-124">Yerel kodda çalıştırmak istediğiniz yönetilen sınıfı için sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eec13-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="eec13-125">Sınıfı, varsayılan bir oluşturucu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eec13-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="eec13-126">AssemblyInfo dosyası, derlemede için dört bölümden oluşan tam sürüm numarası sahip olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="eec13-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="eec13-127">Bu numara, Windows kayıt defterinde sürüm bakımı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eec13-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="eec13-128">Sürüm numaraları hakkında daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="eec13-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2.  <span data-ttu-id="eec13-129">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="eec13-129">On the **Project** menu, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="eec13-130">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="eec13-130">Click the **Compile** tab.</span></span>  
  
4.  <span data-ttu-id="eec13-131">Seçin **kaydetmek için COM birlikte çalışma** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="eec13-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="eec13-132">Projesi derlerken, derleme COM birlikte çalışma için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="eec13-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="eec13-133">Yerel bir uygulama geliştiriyorsanız [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], tıklatarak derleme kullanabilirsiniz **Başvuru Ekle** üzerinde **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="eec13-133">If you are building a native application in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="eec13-134">.NET Framework Araçları'nı kullanarak bir COM aranabilir sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eec13-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
-   <span data-ttu-id="eec13-135">Çalıştırma [Regasm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) aracı.</span><span class="sxs-lookup"><span data-stu-id="eec13-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
 <span data-ttu-id="eec13-136">Bu araç, derleme meta verilerini okur ve gerekli girişleri kayıt defterine ekler.</span><span class="sxs-lookup"><span data-stu-id="eec13-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="eec13-137">Sonuç olarak, COM istemcileri, .NET Framework sınıfları şeffaf bir şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec13-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="eec13-138">Yerel bir COM sınıfı değilmiş gibi derleme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eec13-138">You can use the assembly as if it were a native COM class.</span></span>  
  
 <span data-ttu-id="eec13-139">Herhangi bir dizinde bulunan bir derleme Regasm.exe çalışır ve ardından çalıştırın [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="eec13-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="eec13-140">Derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir çünkü derleme taşıma konum kayıt defteri girdilerini geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="eec13-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec13-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eec13-141">See Also</span></span>  
 [<span data-ttu-id="eec13-142">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="eec13-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="eec13-143">COM Çağrılabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="eec13-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
