---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
description: Visual Studio veya .NET araçları kullanarak bileşen nesne modeli (COM) sarmalayıcıları oluşturun (Tlbimp.exe ve Regasm.exe). Her iki yöntem de iki tür COM sarmalayıcıları üretir.
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 286526c710287e6efa3e49a7f7c55e3687076e29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617398"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="08dfb-104">Nasıl yapılır: COM Sarmalayıcıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08dfb-104">How to: Create COM Wrappers</span></span>

<span data-ttu-id="08dfb-105">Visual Studio 2005 özelliklerini veya .NET Framework araçlarını Tlbimp.exe ve Regasm.exe kullanarak bileşen nesne modeli (COM) sarmalayıcıları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-105">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="08dfb-106">Her iki yöntem de iki tür COM sarmalayıcıları üretir:</span><span class="sxs-lookup"><span data-stu-id="08dfb-106">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="08dfb-107">Yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığından bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="08dfb-107">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="08dfb-108">Yerel bir uygulamada yönetilen bir nesne çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarmalayıcı](../../standard/native-interop/com-callable-wrapper.md) .</span><span class="sxs-lookup"><span data-stu-id="08dfb-108">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="08dfb-109">Visual Studio 2005 ' de COM sarmalayıcısı ' ı projenize bir başvuru olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-109">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="08dfb-110">Yönetilen bir uygulamadaki COM nesnelerini sarın</span><span class="sxs-lookup"><span data-stu-id="08dfb-110">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="08dfb-111">Visual Studio kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08dfb-111">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="08dfb-112">Yönetilen uygulamanız için projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-112">Open the project for your managed application.</span></span>

2. <span data-ttu-id="08dfb-113">**Proje** menüsünde **tüm dosyaları göster**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-113">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="08dfb-114">**Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-114">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="08dfb-115">Başvuru Ekle iletişim kutusunda, **com** sekmesine tıklayın, kullanmak istediğiniz bileşeni seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-115">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="08dfb-116">**Çözüm Gezgini**, com bileşeninin projenizdeki başvurular klasörüne eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-116">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="08dfb-117">Artık COM nesnesine erişmek için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-117">You can now write code to access the COM object.</span></span> <span data-ttu-id="08dfb-118">Nesnesini bildirerek, örneğin, `Imports` Visual Basic için bir deyimle veya C# için bir ifade ile başlayabilirsiniz `Using` .</span><span class="sxs-lookup"><span data-stu-id="08dfb-118">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="08dfb-119">Microsoft Office bileşenleri programlamak istiyorsanız önce [Microsoft Office birincil birlikte çalışma derlemelerini yeniden dağıtılabilir](https://www.microsoft.com/Download/details.aspx?id=3508)olarak yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="08dfb-119">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="08dfb-120">.NET Framework araçlarını kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08dfb-120">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="08dfb-121">[Tlbimp.exe (tür kitaplığı alma programı)](../tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-121">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="08dfb-122">Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verilerini içeren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08dfb-122">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="08dfb-123">Yönetilen nesneleri yerel bir uygulamada sarın</span><span class="sxs-lookup"><span data-stu-id="08dfb-123">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="08dfb-124">Visual Studio kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08dfb-124">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="08dfb-125">Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="08dfb-125">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="08dfb-126">Sınıf parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08dfb-126">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="08dfb-127">AssemblyInfo dosyasında derlemelerinizin dört bölümden oluşan tam bir sürüm numarasına sahip olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-127">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="08dfb-128">Bu sayı, Windows kayıt defterinde sürüm oluşturmayı sürdürmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="08dfb-128">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="08dfb-129">Sürüm numaraları hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="08dfb-129">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="08dfb-130">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-130">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="08dfb-131">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-131">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="08dfb-132">**Com birlikte çalışması Için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="08dfb-132">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="08dfb-133">Projeyi derlediğinizde, derleme otomatik olarak COM birlikte çalışma için kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="08dfb-133">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="08dfb-134">Visual Studio 2005 ' de yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayarak derlemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-134">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="08dfb-135">.NET Framework araçlarını kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08dfb-135">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="08dfb-136">[Regasm.exe (derleme kayıt aracı)](../tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="08dfb-136">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="08dfb-137">Bu araç derleme meta verilerini okur ve gerekli girdileri kayıt defterine ekler.</span><span class="sxs-lookup"><span data-stu-id="08dfb-137">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="08dfb-138">Sonuç olarak, COM istemcileri .NET Framework sınıfları saydam şekilde oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="08dfb-138">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="08dfb-139">Derlemeyi yerel bir COM sınıfı gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-139">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="08dfb-140">Herhangi bir dizinde bulunan bir derlemede Regasm.exe çalıştırabilir ve sonra, genel derleme önbelleğine taşımak için [Gacutil.exe (genel bütünleştirilmiş kod önbelleği aracı)](../tools/gacutil-exe-gac-tool.md) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-140">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="08dfb-141">Derlemenin taşınması konum kayıt defteri girdilerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.</span><span class="sxs-lookup"><span data-stu-id="08dfb-141">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dfb-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08dfb-142">See also</span></span>

- [<span data-ttu-id="08dfb-143">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="08dfb-143">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="08dfb-144">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="08dfb-144">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
