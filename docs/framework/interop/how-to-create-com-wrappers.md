---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121595"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="19771-102">Nasıl yapılır: COM Sarmalayıcıları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="19771-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="19771-103">Visual Studio 2005 özelliklerini veya .NET Framework araçlarını kullanarak Component Object Model (COM) sarmalayıcıları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="19771-104">Her iki yöntem de iki tür COM sarmalayıcı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="19771-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="19771-105">Yönetilen kodda com nesnesini çalıştırmak için bir tür kitaplığından [Runtime Çağrılabilir Sarılayıcı.](../../standard/native-interop/runtime-callable-wrapper.md)</span><span class="sxs-lookup"><span data-stu-id="19771-105">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="19771-106">Yerel bir uygulamada yönetilen bir nesneyi çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarıcı.](../../standard/native-interop/com-callable-wrapper.md)</span><span class="sxs-lookup"><span data-stu-id="19771-106">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="19771-107">Visual Studio 2005'te, PROJENIZE referans olarak COM sarıcıyı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="19771-108">Yönetilen Bir Uygulamada COM Nesnelerini Kaydırma</span><span class="sxs-lookup"><span data-stu-id="19771-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="19771-109">Visual Studio'u kullanarak çalışma zamanı çağrılabilir bir sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19771-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="19771-110">Yönetilen uygulamanız için projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="19771-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="19771-111">**Proje** menüsünde **Tüm Dosyaları Göster'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="19771-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="19771-112">**Proje** menüsünde **Referans Ekle'yi**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="19771-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="19771-113">Başvuru Ekle iletişim kutusunda **COM** sekmesini tıklatın, kullanmak istediğiniz bileşeni seçin ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="19771-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="19771-114">**Çözüm Gezgini'nde,** COM bileşeninin projenizdeki Başvurular klasörüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="19771-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="19771-115">Artık COM nesnesine erişmek için kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="19771-116">Visual Basic deyimi veya C# için `Imports` bir `Using` deyim gibi nesneyi beyan ederek başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="19771-117">Microsoft Office bileşenlerini programlamak istiyorsanız, önce [Microsoft Office Birincil Interop Derlemeleri Yeniden Dağıtılabilir'i yükleyin.](https://www.microsoft.com/Download/details.aspx?id=3508)</span><span class="sxs-lookup"><span data-stu-id="19771-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="19771-118">.NET Framework araçlarını kullanarak çalışma zamanı çağrılabilir sarıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19771-118">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="19771-119">[Tlbimp.exe (Tip Kitaplığı İthalatçısı)](../tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="19771-119">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="19771-120">Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verileri içeren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19771-120">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="19771-121">Yönetilen Nesneleri Yerel Uygulamada Kaydırma</span><span class="sxs-lookup"><span data-stu-id="19771-121">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="19771-122">Visual Studio'u kullanarak com çağrılabilir sarıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19771-122">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="19771-123">Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19771-123">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="19771-124">Sınıfın parametresiz bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19771-124">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="19771-125">AssemblyInfo dosyasında assemblyiniz için tam dört bölümlü bir sürüm numarasına sahip olduğunuzu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="19771-125">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="19771-126">Bu numara, Windows kayıt defterinde sürüm tutmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19771-126">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="19771-127">Sürüm numaraları hakkında daha fazla bilgi için [Montaj Sürümü'ne](../../standard/assembly/versioning.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="19771-127">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="19771-128">**Proje** menüsünde **Özellikler'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="19771-128">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="19771-129">**Derle** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="19771-129">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="19771-130">COM **interop** onay kutusunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="19771-130">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="19771-131">Projeyi oluşturduğunuzda, derleme otomatik olarak COM interop için kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="19771-131">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="19771-132">Visual Studio 2005'te yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Referans Ekle'yi** tıklatarak derlemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-132">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="19771-133">.NET Framework araçlarını kullanarak com çağrılabilir sarıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19771-133">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="19771-134">[Regasm.exe (Montaj Kayıt Aracı)](../tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="19771-134">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="19771-135">Bu araç derleme meta verilerini okur ve gerekli girişleri kayıt defterine ekler.</span><span class="sxs-lookup"><span data-stu-id="19771-135">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="19771-136">Sonuç olarak, COM istemcileri .NET Framework sınıflarını saydam olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="19771-136">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="19771-137">Derlemeyi yerel bir COM sınıfıymuş gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-137">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="19771-138">Regasm.exe'yi herhangi bir dizinde bulunan bir derlemede çalıştırabilir ve ardından genel derleme önbelleğine taşımak için [Gacutil.exe'yi (Genel Derleme Önbellek Aracı)](../tools/gacutil-exe-gac-tool.md) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19771-138">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="19771-139">Derlemenin taşınması konum kayıt defteri girişlerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.</span><span class="sxs-lookup"><span data-stu-id="19771-139">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19771-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19771-140">See also</span></span>

- [<span data-ttu-id="19771-141">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="19771-141">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="19771-142">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="19771-142">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
