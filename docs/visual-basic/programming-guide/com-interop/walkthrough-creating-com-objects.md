---
title: 'İzlenecek yol: COM nesneleri oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5d00aff07358a0c40159fde9c12c70e0842d848b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338614"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="875f0-102">İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="875f0-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="875f0-103">Yeni uygulamalar veya bileşenler oluştururken .NET Framework derlemeleri oluşturmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="875f0-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="875f0-104">Ancak Visual Basic Ayrıca, bir .NET Framework bileşenini COM 'da kullanıma sunmayı da kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="875f0-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="875f0-105">Bu, COM bileşenleri gerektiren önceki uygulama paketleri için yeni bileşenler sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="875f0-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="875f0-106">Bu izlenecek yol, .NET Framework nesnelerini com nesneleri olarak göstermek için Visual Basic, hem hem de COM sınıf şablonuyla birlikte kullanmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="875f0-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="875f0-107">COM nesnelerini kullanıma almanın en kolay yolu COM sınıf şablonunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="875f0-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="875f0-108">COM sınıfı şablonu yeni bir sınıf oluşturur ve ardından projeyi bir COM nesnesi olarak sınıf ve birlikte çalışabilirlik katmanını oluşturacak şekilde yapılandırır ve işletim sistemine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="875f0-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="875f0-109">Yönetilmeyen kodun kullanması için Visual Basic bir COM nesnesi olarak oluşturulan bir sınıfı kullanıma sunabilseniz de, bu gerçek bir COM nesnesi değildir ve Visual Basic tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="875f0-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="875f0-110">Daha fazla bilgi için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="875f0-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="875f0-111">COM sınıf şablonunu kullanarak bir COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="875f0-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="875f0-112">Yeni **Proje**' ye tıklayarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="875f0-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="875f0-113">**Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="875f0-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="875f0-114">**Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="875f0-115">Yeni proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="875f0-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="875f0-116">**Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="875f0-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="875f0-117">**Yeni öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="875f0-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="875f0-118">**Şablonlar** listesinden **com sınıfı** ' nı seçin ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="875f0-119">Visual Basic yeni bir sınıf ekler ve COM birlikte çalışması için yeni projeyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="875f0-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="875f0-120">COM sınıfına özellikler, Yöntemler ve olaylar gibi bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="875f0-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="875f0-121">**Build** menüsünden **Build ClassLibrary1** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="875f0-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="875f0-122">Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.</span><span class="sxs-lookup"><span data-stu-id="875f0-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="875f0-123">Com sınıf şablonu olmadan COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="875f0-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="875f0-124">COM sınıfı şablonunu kullanmak yerine el ile bir COM sınıfı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="875f0-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="875f0-125">Bu yordam, komut satırından çalışırken veya COM nesnelerinin nasıl tanımlandığı hakkında daha fazla denetim istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="875f0-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="875f0-126">Projenizi bir COM nesnesi oluşturacak şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="875f0-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="875f0-127">**NewProject**' i tıklatarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="875f0-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="875f0-128">**Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="875f0-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="875f0-129">**Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="875f0-130">Yeni proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="875f0-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="875f0-131">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="875f0-132">**Proje Tasarımcısı** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="875f0-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="875f0-133">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="875f0-134">**Com birlikte çalışması Için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="875f0-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="875f0-135">Bir COM nesnesi oluşturmak için sınıfınıza kodu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="875f0-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="875f0-136">**Çözüm Gezgini**, kodunu göstermek için **Class1. vb** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="875f0-137">Sınıfı `ComClass1`olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="875f0-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="875f0-138">`ComClass1`için aşağıdaki sabitleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="875f0-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="875f0-139">Bunlar, COM nesnelerinin sahip olması için gerekli olan genel benzersiz tanımlayıcı (GUID) sabitlerini depolayacaktır.</span><span class="sxs-lookup"><span data-stu-id="875f0-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="875f0-140">**Araçlar** menüsünde **GUID oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="875f0-141">**GUID oluştur** iletişim kutusunda, **kayıt defteri biçimi** ' ne ve ardından **Kopyala**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="875f0-142">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="875f0-143">`ClassId` için boş dizeyi, baştaki ve sondaki ayraçları kaldırarak GUID ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="875f0-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="875f0-144">Örneğin, Guidgen tarafından belirtilen GUID `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`, kodunuzun aşağıdaki gibi görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="875f0-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="875f0-145">Aşağıdaki örnekte olduğu gibi `InterfaceId` ve `EventsId` sabitleri için önceki adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="875f0-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="875f0-146">GUID 'lerin yeni ve benzersiz olduğundan emin olun; Aksi halde, COM bileşeniniz diğer COM bileşenleriyle çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="875f0-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="875f0-147">Aşağıdaki örnekte olduğu gibi, sınıf KIMLIĞI, arabirim KIMLIĞI ve olay KIMLIĞI için GUID 'Leri belirterek `ComClass1``ComClass` özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="875f0-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="875f0-148">COM sınıflarının parametresiz `Public Sub New()` oluşturucusu olmalıdır veya sınıf doğru şekilde kayıt olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="875f0-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="875f0-149">Sınıfına parametresiz bir Oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="875f0-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="875f0-150">Sınıfa özellikler, Yöntemler ve olaylar ekleyin ve bunu bir `End Class` ifadesiyle sona erdirin.</span><span class="sxs-lookup"><span data-stu-id="875f0-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="875f0-151">**Build** menüsünden **Build Solution** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="875f0-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="875f0-152">Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.</span><span class="sxs-lookup"><span data-stu-id="875f0-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="875f0-153">Visual Basic ile oluşturduğunuz COM nesneleri, doğru COM nesneleri olmadığından diğer Visual Basic uygulamalar tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="875f0-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="875f0-154">Bu tür COM nesnelerine başvuru ekleme girişimleri bir hata oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="875f0-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="875f0-155">Ayrıntılar için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="875f0-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="875f0-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="875f0-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="875f0-157">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="875f0-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="875f0-158">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="875f0-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="875f0-159">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="875f0-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="875f0-160">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="875f0-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="875f0-161">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="875f0-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
