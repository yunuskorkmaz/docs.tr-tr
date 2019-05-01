---
title: 'İzlenecek yol: Visual Basic ile COM nesneleri oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 97e917d568b31860979e54598350d1ae7a6fdb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022317"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="e569d-102">İzlenecek yol: Visual Basic ile COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e569d-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="e569d-103">Yeni uygulama veya bileşenler oluştururken, .NET Framework derlemeleri oluşturmak idealdir.</span><span class="sxs-lookup"><span data-stu-id="e569d-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="e569d-104">Ancak, Visual Basic ayrıca, bir .NET Framework bileşenini vystavit kullanıma sunmak kolaylaştırır</span><span class="sxs-lookup"><span data-stu-id="e569d-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="e569d-105">Bu yeni bileşenler için COM bileşenlerini gerektiren önceki uygulama paketlerini vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e569d-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="e569d-106">Bu izlenecek yol göstermek için Visual Basic kullanmayı gösteren [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nesneler COM nesneleri, hem ile hem de olmadan COM sınıf şablonu olarak.</span><span class="sxs-lookup"><span data-stu-id="e569d-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="e569d-107">COM nesnelerini kullanıma sunmak için en kolay yolu, COM sınıf şablonu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e569d-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="e569d-108">COM sınıf şablonu, yeni bir sınıf oluşturur ve projenize bir COM nesnesi olarak sınıfı ve birlikte çalışabilirlik katman oluşturmak ve işletim sistemi ile kaydetmek için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e569d-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e569d-109">Visual Basic'te kullanmak için yönetilmeyen kod için bir COM nesnesi olarak oluşturulmuş bir sınıf görülebileceği da olsa da, doğru bir COM nesnesi değil ve Visual Basic tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e569d-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="e569d-110">Daha fazla bilgi için [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e569d-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="e569d-111">COM sınıf şablonu kullanarak bir COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e569d-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="e569d-112">Yeni bir Windows uygulaması projesi açın **dosya** tıklayarak menü **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="e569d-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="e569d-113">İçinde **yeni proje** iletişim kutusunun altında **proje türleri** alan, Windows seçili olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e569d-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="e569d-114">Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e569d-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="e569d-115">Yeni Proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e569d-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="e569d-116">Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e569d-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="e569d-117">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e569d-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="e569d-118">Seçin **COM sınıfı** gelen **şablonları** listeleyin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e569d-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="e569d-119">Visual Basic, yeni bir sınıf ekler ve yeni proje COM birlikte çalışması için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e569d-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="e569d-120">Kod gibi özellikleri, yöntemleri ve olayları COM sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e569d-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="e569d-121">Seçin **derleme ClassLibrary1** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e569d-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="e569d-122">Visual Basic derleme yapıları ve COM nesnesi işletim sistemi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e569d-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="e569d-123">COM sınıf şablonu olmadan COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e569d-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="e569d-124">Ayrıca, bir COM sınıfı COM sınıf şablonu kullanmak yerine el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e569d-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="e569d-125">Bu yordam, komut satırından çalışırken veya COM nesnelerinin nasıl tanımlandığı hakkında daha fazla denetime istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e569d-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="e569d-126">Bir COM nesnesi oluşturmak için projenizi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e569d-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="e569d-127">Yeni bir Windows uygulaması projesi açın **dosya** tıklayarak menü **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="e569d-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="e569d-128">İçinde **yeni proje** iletişim kutusunun altında **proje türleri** alan, Windows seçili olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e569d-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="e569d-129">Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e569d-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="e569d-130">Yeni Proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e569d-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="e569d-131">İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e569d-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="e569d-132">**Proje Tasarımcısı** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e569d-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="e569d-133">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="e569d-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="e569d-134">Seçin **kaydetme COM birlikte çalışması için** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e569d-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="e569d-135">Bir COM nesnesi oluşturmak için kod Sınıfınız içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e569d-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="e569d-136">İçinde **Çözüm Gezgini**, çift **Class1.vb** kodunu görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="e569d-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="e569d-137">Sınıfı Yeniden Adlandır `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="e569d-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="e569d-138">Aşağıdaki sabitleri ekleyin `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="e569d-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="e569d-139">Bunlar, COM nesneleri için gerekli olan genel benzersiz tanıtıcısı (GUID) sabitleri depolar.</span><span class="sxs-lookup"><span data-stu-id="e569d-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="e569d-140">Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="e569d-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="e569d-141">İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**.</span><span class="sxs-lookup"><span data-stu-id="e569d-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="e569d-142">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e569d-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="e569d-143">Boş bir dize yerine `ClassId` başında kaldırma ve sondaki GUID ile küme ayraçları.</span><span class="sxs-lookup"><span data-stu-id="e569d-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="e569d-144">Örneğin, GUID GUIDgen tarafından sağlanmışsa `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` sonra kodunuzu aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="e569d-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="e569d-145">Önceki adımları yineleyin `InterfaceId` ve `EventsId` sabitleri, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="e569d-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e569d-146">GUID'ler yeni ve benzersiz olduğundan emin olun; Aksi takdirde, COM bileşeni ile diğer COM bileşenleri çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="e569d-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="e569d-147">Ekleme `ComClass` özniteliğini `ComClass1`, aşağıdaki örnekte olduğu gibi sınıf kimliği, arabirim kimliği ve olay kimliği GUID'leri belirtme:</span><span class="sxs-lookup"><span data-stu-id="e569d-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="e569d-148">COM sınıfları bir parametresiz olmalıdır `Public Sub New()` Oluşturucusu veya sınıf kaydetme doğru.</span><span class="sxs-lookup"><span data-stu-id="e569d-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="e569d-149">Parametresiz bir oluşturucu, sınıfı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e569d-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="e569d-150">İle biten sınıfı özellikleri, yöntemleri ve olayları eklemek bir `End Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e569d-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="e569d-151">Seçin **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e569d-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="e569d-152">Visual Basic derleme yapıları ve COM nesnesi işletim sistemi ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e569d-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e569d-153">COM nesneleri doğru olmadığı için Visual Basic ile oluşturduğunuz COM nesneleri başka bir Visual Basic uygulama tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e569d-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="e569d-154">Bu tür COM nesnelerine başvurular ekleme girişimleri hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e569d-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="e569d-155">Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e569d-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e569d-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e569d-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="e569d-157">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="e569d-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="e569d-158">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="e569d-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="e569d-159">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="e569d-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="e569d-160">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="e569d-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="e569d-161">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="e569d-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
