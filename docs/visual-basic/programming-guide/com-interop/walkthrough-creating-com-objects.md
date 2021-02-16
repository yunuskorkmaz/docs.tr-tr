---
description: 'Daha fazla bilgi edinin: Izlenecek yol: Visual Basic COM nesneleri oluşturma'
title: 'İzlenecek yol: COM Nesneleri Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 469466189e264253f3588a0a2735afe651bbd36f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427277"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="0c2d3-103">İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c2d3-103">Walkthrough: Creating COM Objects with Visual Basic</span></span>

<span data-ttu-id="0c2d3-104">Yeni uygulamalar veya bileşenler oluştururken .NET Framework derlemeleri oluşturmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-104">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="0c2d3-105">Ancak Visual Basic Ayrıca, bir .NET Framework bileşenini COM 'da kullanıma sunmayı da kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-105">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="0c2d3-106">Bu, COM bileşenleri gerektiren önceki uygulama paketleri için yeni bileşenler sağlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-106">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="0c2d3-107">Bu izlenecek yol, .NET Framework nesnelerini com nesneleri olarak göstermek için Visual Basic, hem hem de COM sınıf şablonuyla birlikte kullanmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-107">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="0c2d3-108">COM nesnelerini kullanıma almanın en kolay yolu COM sınıf şablonunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-108">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="0c2d3-109">Bu şablon yeni bir sınıf oluşturur, sonra projenizi bir COM nesnesi olarak birlikte çalışabilirlik katmanıyla oluşturacak şekilde yapılandırır ve işletim sistemine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-109">This template creates a new class, then configures your project to generate the class with an interoperability layer as a COM object, and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c2d3-110">Yönetilmeyen kodun kullanması için Visual Basic bir COM nesnesi olarak oluşturulan bir sınıfı kullanıma sunabilseniz de, bu gerçek bir COM nesnesi değildir ve Visual Basic tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-110">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="0c2d3-111">Daha fazla bilgi için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="0c2d3-111">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="0c2d3-112">COM sınıf şablonunu kullanarak bir COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0c2d3-112">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="0c2d3-113">Yeni **Proje**' ye tıklayarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-113">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="0c2d3-114">**Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-114">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="0c2d3-115">**Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-115">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="0c2d3-116">Yeni proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-116">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="0c2d3-117">**Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-117">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="0c2d3-118">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-118">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="0c2d3-119">**Şablonlar** listesinden **com sınıfı** ' nı seçin ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-119">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="0c2d3-120">Visual Basic yeni bir sınıf ekler ve COM birlikte çalışması için yeni projeyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-120">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="0c2d3-121">COM sınıfına özellikler, Yöntemler ve olaylar gibi bir kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-121">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="0c2d3-122">**Build** menüsünden **Build ClassLibrary1** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-122">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="0c2d3-123">Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-123">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="0c2d3-124">Com sınıf şablonu olmadan COM nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c2d3-124">Creating COM Objects without the COM Class Template</span></span>  

 <span data-ttu-id="0c2d3-125">COM sınıfı şablonunu kullanmak yerine el ile bir COM sınıfı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-125">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="0c2d3-126">Bu yordam, komut satırından çalışırken veya COM nesnelerinin nasıl tanımlandığı hakkında daha fazla denetim istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-126">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="0c2d3-127">Projenizi bir COM nesnesi oluşturacak şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0c2d3-127">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="0c2d3-128">**NewProject**' i tıklatarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-128">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="0c2d3-129">**Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-129">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="0c2d3-130">**Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-130">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="0c2d3-131">Yeni proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-131">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="0c2d3-132">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-132">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="0c2d3-133">**Proje Tasarımcısı** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-133">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="0c2d3-134">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-134">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="0c2d3-135">**Com birlikte çalışması Için kaydol** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-135">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="0c2d3-136">Bir COM nesnesi oluşturmak için sınıfınıza kodu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0c2d3-136">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="0c2d3-137">**Çözüm Gezgini**, kodunu göstermek için **Class1. vb** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-137">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="0c2d3-138">Sınıfını olarak yeniden adlandırın `ComClass1` .</span><span class="sxs-lookup"><span data-stu-id="0c2d3-138">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="0c2d3-139">Aşağıdaki sabitleri öğesine ekleyin `ComClass1` .</span><span class="sxs-lookup"><span data-stu-id="0c2d3-139">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="0c2d3-140">Bunlar, COM nesnelerinin sahip olması için gerekli olan genel benzersiz tanımlayıcı (GUID) sabitlerini depolayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-140">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="0c2d3-141">**Araçlar** menüsünde **GUID oluştur**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="0c2d3-142">**GUID oluştur** iletişim kutusunda, **kayıt defteri biçimi** ' ne ve ardından **Kopyala**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="0c2d3-143">**Çıkış**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-143">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="0c2d3-144">İçin boş dizeyi `ClassId` GUID ile değiştirin, baştaki ve sondaki ayraçları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="0c2d3-145">Örneğin, Guidgen tarafından belirtilen GUID ise `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` kodunuzun aşağıdaki gibi görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="0c2d3-146">`InterfaceId`Aşağıdaki örnekte olduğu gibi, ve sabitleri için önceki adımları tekrarlayın `EventsId` .</span><span class="sxs-lookup"><span data-stu-id="0c2d3-146">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="0c2d3-147">GUID 'lerin yeni ve benzersiz olduğundan emin olun; Aksi halde, COM bileşeniniz diğer COM bileşenleriyle çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-147">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="0c2d3-148">`ComClass` `ComClass1` Aşağıdaki örnekte olduğu gıbı sınıf kimliği, arabirim kimliği ve olay kimliği Için GUID 'leri belirterek özniteliğini öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0c2d3-148">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="0c2d3-149">COM sınıflarının parametresiz bir oluşturucusu olmalıdır `Public Sub New()` veya sınıf doğru şekilde kayıt olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-149">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="0c2d3-150">Sınıfına parametresiz bir Oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0c2d3-150">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="0c2d3-151">Sınıfa özellikler, Yöntemler ve olaylar ekleyin ve bir `End Class` ifadesiyle biter.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-151">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="0c2d3-152">**Build** menüsünden **Build Solution** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-152">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="0c2d3-153">Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-153">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0c2d3-154">Visual Basic ile oluşturduğunuz COM nesneleri, doğru COM nesneleri olmadığından diğer Visual Basic uygulamalar tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-154">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="0c2d3-155">Bu tür COM nesnelerine başvuru ekleme girişimleri bir hata oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-155">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="0c2d3-156">Ayrıntılar için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="0c2d3-156">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c2d3-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c2d3-157">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="0c2d3-158">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="0c2d3-158">COM Interop</span></span>](index.md)
- [<span data-ttu-id="0c2d3-159">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="0c2d3-159">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="0c2d3-160">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="0c2d3-160">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="0c2d3-161">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="0c2d3-161">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="0c2d3-162">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="0c2d3-162">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
