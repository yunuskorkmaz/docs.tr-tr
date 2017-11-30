---
title: "İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d6906c58431a0e844e8f430ade10ae819e77ff2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="c4bd6-102">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4bd6-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="c4bd6-103">Visual Basic sınıflardan türetilemeyeceğini `Public` olanlar'ın önceki sürümlerinde oluşturulan COM nesnelerini sınıflarda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4bd6-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="c4bd6-104">Özellikleri ve yöntemleri COM nesneleri devralınan sınıfların geçersiz kılındı gibi özellikleri olarak aşırı yüklendi ve herhangi bir taban sınıf yöntemlerini geçersiz veya aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="c4bd6-105">COM nesneleri içinden devralma yeniden derleyin istemediğiniz varolan bir sınıf kitaplığı olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="c4bd6-106">Aşağıdaki yordamda, Visual Basic 6.0 bir sınıfı içeren bir COM nesnesi oluşturmak ve temel sınıf olarak kullanmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="c4bd6-107">Bu kılavuzda kullanılan COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c4bd6-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="c4bd6-108">Visual Basic 6. 0'da, yeni bir ActiveX DLL projesi açın.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="c4bd6-109">Adlı bir proje `Project1` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-109">A project named `Project1` is created.</span></span> <span data-ttu-id="c4bd6-110">Adlı bir sınıf sahip `Class1`.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="c4bd6-111">İçinde **Proje Gezgini**, sağ **Project1**ve ardından **Project1 özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="c4bd6-112">**Proje özelliklerini** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="c4bd6-113">Üzerinde **genel** sekmesinde **proje özelliklerini** iletişim kutusunda, proje adını yazarak değiştirme `ComObject1` içinde **proje adı** alan.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="c4bd6-114">İçinde **Proje Gezgini**, sağ `Class1`ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="c4bd6-115">**Özellikleri** sınıfı için penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="c4bd6-116">Değişiklik `Name` özelliğine `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="c4bd6-117">İçinde **Proje Gezgini**, sağ `MathFunctions`ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="c4bd6-118">**Kod düzenleyicisinde** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="c4bd6-119">Özellik değeri tutmak için yerel bir değişken ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="c4bd6-120">Özellik ekleme `Let` ve özellik `Get` özellik yordamları:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="c4bd6-121">Bir işlevi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="c4bd6-122">Oluşturma ve tıklayarak COM nesnesi kaydetme **olun ComObject1.dll** üzerinde **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4bd6-123">Ayrıca ile oluşturulan bir sınıf getirebilir rağmen [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bir COM nesnesi olarak doğru bir COM nesnesi değil ve bu kılavuzda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-123">Although you can also expose a class created with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="c4bd6-124">Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c4bd6-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="c4bd6-125">Birlikte çalışma derlemeleri</span><span class="sxs-lookup"><span data-stu-id="c4bd6-125">Interop Assemblies</span></span>  
 <span data-ttu-id="c4bd6-126">Aşağıdaki yordamda, yönetilmeyen kod (örneğin, bir COM nesnesi) ve yönetilen kod arasında bir köprü görevi gören bir birlikte çalışma derlemesi oluşturacak [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses.</span></span> <span data-ttu-id="c4bd6-127">Birlikte çalışma derlemesi, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gibi birçok COM ile çalışma ayrıntılarını nesneleri tanıtıcıları oluşturur *birlikte çalışma hazırlama*, işlemi paketleme parametreler ve dönüş değerleri eşdeğer veri türleri için taşırken ve COM nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-127">The interop assembly that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="c4bd6-128">Başvuru [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulama noktalarına birlikte çalışma derlemesi, gerçek COM nesnesi değil.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-128">The reference in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="c4bd6-129">Visual Basic 2005 ve sonraki sürümler ile COM nesnesini kullanma</span><span class="sxs-lookup"><span data-stu-id="c4bd6-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="c4bd6-130">Yeni bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows uygulama projesi.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-130">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="c4bd6-131">Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="c4bd6-132">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="c4bd6-133">Üzerinde **COM** sekmesinde, çift `ComObject1` içinde **bileşen adı** listesinde ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="c4bd6-134">Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="c4bd6-135">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="c4bd6-136">İçinde **şablonları** bölmesinde tıklatın **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="c4bd6-137">Varsayılan dosya adı `Class1.vb`, görünür **adı** alan.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="c4bd6-138">Bu alan MathClass.vb tıklatın geçip **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="c4bd6-139">Bu adlı bir sınıf oluşturur `MathClass`ve kendi kod görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="c4bd6-140">En üst kısmına aşağıdaki kodu ekleyin `MathClass` COM sınıfından için.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="c4bd6-141">Aşağıdaki kodu ekleyerek temel sınıfın genel yöntem aşırı `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="c4bd6-142">Aşağıdaki kodu ekleyerek devralınan sınıfını genişleten `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="c4bd6-143">Yeni sınıf COM nesnesi temel sınıfının özelliklerini devralır, bir yöntemi aşırı yüklemeleri ve sınıf genişletmek için yeni bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="c4bd6-144">Devralınan sınıfı test etmek için</span><span class="sxs-lookup"><span data-stu-id="c4bd6-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="c4bd6-145">Düğme başlangıç formunuza eklemek ve kendi kod görüntülemek için çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="c4bd6-146">Düğmenin içinde `Click` olay işleyicisi yordamı, bir örneğini oluşturmak için aşağıdaki kodu ekleyin `MathClass` ve aşırı yüklenmiş yöntemler çağırın:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="c4bd6-147">F5 tuşuna basarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="c4bd6-148">Form düğmeyi tıkladığınızda `AddNumbers` yöntemi ile ilk çağrılır `Short` veri türü numaraları ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygun yöntemi temel sınıfından seçer.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="c4bd6-149">İkinci çağrı `AddNumbers` aşırı yükleme yönteminden yönlendirildiği `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="c4bd6-150">Üçüncü çağrıları çağrı `SubtractNumbers` sınıfını genişleten yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="c4bd6-151">Taban sınıfı özelliğinde ayarlanır ve değer görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c4bd6-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c4bd6-152">Next Steps</span></span>  
 <span data-ttu-id="c4bd6-153">Fark etmiş aşırı yüklenmiş `AddNumbers` işlevi aynı veri türünde COM nesnesinin temel sınıfından devralınan yöntemi olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="c4bd6-154">Visual Basic 6.0 16 bit tamsayı olarak bağımsız değişkenleri ve parametreleri temel sınıf yönteminin tanımlı, ancak türü 16 bit tamsayı olarak gösterilir çünkü `Short` Visual Basic sonraki sürümlerinde.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="c4bd6-155">Yeni işlev 32-bit tamsayı kabul eder ve temel sınıf işlevi overloads.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="c4bd6-156">COM nesneleri ile çalışırken, parametre boyut ve veri türlerini doğruladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="c4bd6-157">Örneğin, bir Visual Basic 6.0 koleksiyon nesnesi bağımsız değişken olarak kabul eden bir COM nesnesi kullanırken, Visual Basic daha sonraki bir sürümü koleksiyondan sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="c4bd6-158">Özellikleri ve yöntemleri COM sınıflardan devralınan bir yerel özellik veya bir özellik değiştiren veya temel bir COM sınıfından devralınan yöntemini bildirebilir anlamı kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="c4bd6-159">Devralınan COM özelliklerini geçersiz kılma kuralları, diğer özellikleri ve yöntemleri aşağıdaki istisnalar dışında geçersiz kılma için kurallar benzerdir:</span><span class="sxs-lookup"><span data-stu-id="c4bd6-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="c4bd6-160">Herhangi bir özelliği veya bir COM sınıfından devralınan yöntemi geçersiz kılarsanız, tüm diğer devralınan özellikleri ve yöntemleri geçersiz kılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="c4bd6-161">Kullandığınız özellikler `ByRef` parametreleri geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4bd6-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4bd6-162">See Also</span></span>  
 [<span data-ttu-id="c4bd6-163">.NET Framework uygulamalarında COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="c4bd6-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="c4bd6-164">Inherits deyimi</span><span class="sxs-lookup"><span data-stu-id="c4bd6-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="c4bd6-165">Short veri türü</span><span class="sxs-lookup"><span data-stu-id="c4bd6-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
