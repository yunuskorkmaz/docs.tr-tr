---
title: 'İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e660d672fc32455cee349dc44ad20c3244c087b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="96760-102">İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96760-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="96760-103">Yeni uygulamalar veya bileşenleri oluştururken, .NET Framework derlemeleri oluşturma en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="96760-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="96760-104">Ancak, Visual Basic ayrıca com .NET Framework bileşenine kullanıma sunmak kolaylaştırır</span><span class="sxs-lookup"><span data-stu-id="96760-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="96760-105">Bu, COM bileşenlerini gerektiren önceki uygulama paketleri için yeni bileşenler sağlamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="96760-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="96760-106">Bu anlatımda Visual Basic kullanıma sunmak için nasıl kullanılacağı gösterilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nesneleri COM nesneleri, hem ile hem de COM sınıfı şablonu olmadan olarak.</span><span class="sxs-lookup"><span data-stu-id="96760-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="96760-107">COM nesneleri kullanıma sunmak için en kolay yolu, COM sınıfı şablonu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="96760-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="96760-108">COM sınıfı şablonu yeni bir sınıf oluşturur ve projenizin COM nesnesi olarak sınıfı ve birlikte çalışabilirlik katmanı oluşturmak ve işletim sistemi ile kaydetmek için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="96760-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96760-109">Visual Basic'te kullanmak yönetilmeyen kod için bir COM nesnesi olarak oluşturulmuş bir sınıf da getirebilir rağmen doğru bir COM nesnesi değil ve Visual Basic tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="96760-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="96760-110">Daha fazla bilgi için bkz: [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="96760-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="96760-111">COM sınıfı şablonu kullanarak bir COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="96760-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="96760-112">Yeni bir Windows uygulaması projesinden açın **dosya** menüsünde tıklayarak **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="96760-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="96760-113">İçinde **yeni proje** iletişim kutusunda altında **proje türleri** alan, Windows işaretli olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="96760-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="96760-114">Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="96760-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="96760-115">Yeni Proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96760-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="96760-116">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="96760-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="96760-117">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96760-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="96760-118">Seçin **COM sınıfı** gelen **şablonları** listeleyin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="96760-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="96760-119">Visual Basic yeni bir sınıf ekler ve yeni proje COM birlikte çalışma için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="96760-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="96760-120">Özellikleri, yöntemleri ve olayları gibi kodu COM sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="96760-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="96760-121">Seçin **yapı ClassLibrary1** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="96760-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="96760-122">Visual Basic derleme oluşturur ve COM nesnesi işletim sistemi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="96760-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="96760-123">COM sınıfı şablonu olmadan COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="96760-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="96760-124">COM sınıfı şablonu kullanmak yerine el ile bir COM sınıfı de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96760-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="96760-125">Bu yordam, komut satırından çalışırken veya COM nesneleri nasıl tanımlanan üzerinde daha fazla denetim istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="96760-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="96760-126">Bir COM nesnesi oluşturmak için projenizi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="96760-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="96760-127">Yeni bir Windows uygulaması projesinden açın **dosya** menüsünde tıklayarak **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="96760-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="96760-128">İçinde **yeni proje** iletişim kutusunda altında **proje türleri** alan, Windows işaretli olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="96760-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="96760-129">Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="96760-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="96760-130">Yeni Proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96760-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="96760-131">İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="96760-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="96760-132">**Proje Tasarımcısı** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96760-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="96760-133">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="96760-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="96760-134">Seçin **kaydetmek için COM birlikte çalışma** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="96760-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="96760-135">Bir COM nesnesi oluşturmak için kod sınıfınızda ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="96760-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="96760-136">İçinde **Çözüm Gezgini**, çift **Class1.vb'ye** kendi kodumu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="96760-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="96760-137">Sınıfı için yeniden adlandırma `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="96760-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="96760-138">Aşağıdaki sabitleri ekleyin `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="96760-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="96760-139">Bunlar COM nesneleri sahip olması gereken genel benzersiz tanımlayıcı (GUID) sabitleri depolar.</span><span class="sxs-lookup"><span data-stu-id="96760-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="96760-140">Üzerinde **Araçları** menüsünde tıklatın **Create GUID**.</span><span class="sxs-lookup"><span data-stu-id="96760-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="96760-141">İçinde **Create GUID** iletişim kutusu, tıklatın **kayıt defteri biçimi** ve ardından **kopya**.</span><span class="sxs-lookup"><span data-stu-id="96760-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="96760-142">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="96760-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="96760-143">Boş dize Değiştir `ClassId` kaldırarak başında ve sonunda GUID ile küme ayraçları.</span><span class="sxs-lookup"><span data-stu-id="96760-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="96760-144">Örneğin, GUID GUIDgen tarafından sağlanan ise `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` sonra kodunuzu aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="96760-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="96760-145">İçin önceki adımı yineleyin `InterfaceId` ve `EventsId` aşağıdaki örnekteki gibi sabitleri.</span><span class="sxs-lookup"><span data-stu-id="96760-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="96760-146">GUID'lerin yeni ve benzersiz olduğundan emin olun; Aksi takdirde, COM bileşeni diğer COM bileşenleri ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="96760-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="96760-147">Ekleme `ComClass` özniteliğini `ComClass1`, GUID'lerini aşağıdaki örnekteki sınıfı kimliği, arabirim kimliği ve olayları kimliği belirtme:</span><span class="sxs-lookup"><span data-stu-id="96760-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="96760-148">COM sınıfları bir parametresiz olmalıdır `Public Sub New()` Oluşturucusu veya sınıfın kaydettirilemedi doğru.</span><span class="sxs-lookup"><span data-stu-id="96760-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="96760-149">Parametresiz bir kurucusu sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="96760-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="96760-150">Özellikleri, yöntemleri ve olayları ile biten sınıfına ekleyin bir `End Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="96760-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="96760-151">Seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="96760-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="96760-152">Visual Basic derleme oluşturur ve COM nesnesi işletim sistemi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="96760-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="96760-153">Doğru COM nesneleri olmadıklarından Visual Basic ile oluşturduğunuz COM nesneleri başka bir Visual Basic uygulama tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="96760-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="96760-154">Bu tür COM nesnelerine başvurular ekleme girişimleri bir hata ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="96760-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="96760-155">Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="96760-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96760-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96760-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="96760-157">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="96760-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="96760-158">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="96760-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="96760-159">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="96760-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="96760-160">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="96760-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="96760-161">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="96760-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
