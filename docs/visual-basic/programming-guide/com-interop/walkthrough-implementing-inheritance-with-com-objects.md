---
title: 'İzlenecek yol: (Visual Basic) COM nesnelerinde kalıtım uygulama'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: d3814dddb0e39bf986e8d6ee88b3c7b4ec759748
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980457"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="7d66b-102">İzlenecek yol: (Visual Basic) COM nesnelerinde kalıtım uygulama</span><span class="sxs-lookup"><span data-stu-id="7d66b-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="7d66b-103">Visual Basic sınıfları türetebilirsiniz `Public` olanlar Visual Basic'in önceki sürümlerinde oluşturulan COM nesnelerini sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7d66b-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="7d66b-104">Özellikler ve yöntemler COM nesnelerden devralınan sınıf geçersiz kılınan gibi özellikleri olarak aşırı ve herhangi bir taban sınıf yöntemlerini geçersiz kılınmış veya aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="7d66b-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="7d66b-105">COM nesneleri içinden devralma derlemeniz istemediğiniz var olan bir sınıf kitaplığı olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7d66b-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="7d66b-106">Aşağıdaki yordam Visual Basic 6.0 bir sınıf içeren bir COM nesnesi oluşturur ve ardından bir temel sınıf olarak kullanmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="7d66b-107">Bu kılavuzda kullanılan COM nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7d66b-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="7d66b-108">Visual Basic 6. 0'da, yeni bir ActiveX DLL projesi açın.</span><span class="sxs-lookup"><span data-stu-id="7d66b-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="7d66b-109">Adlı bir proje `Project1` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7d66b-109">A project named `Project1` is created.</span></span> <span data-ttu-id="7d66b-110">Adlı bir sınıf sahip `Class1`.</span><span class="sxs-lookup"><span data-stu-id="7d66b-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="7d66b-111">İçinde **Proje Gezgini**, sağ **Project1**ve ardından **Project1 özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="7d66b-112">**Proje özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="7d66b-113">Üzerinde **genel** sekmesinde **proje özellikleri** iletişim kutusunda, proje adını yazarak değiştirin `ComObject1` içinde **proje adı** alan.</span><span class="sxs-lookup"><span data-stu-id="7d66b-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="7d66b-114">İçinde **Proje Gezgini**, sağ `Class1`ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="7d66b-115">**Özellikleri** sınıfı penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="7d66b-116">Değişiklik `Name` özelliğini `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="7d66b-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="7d66b-117">İçinde **Proje Gezgini**, sağ `MathFunctions`ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="7d66b-118">**Kod Düzenleyicisi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="7d66b-119">Özellik değerini tutacak bir yerel değişken ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7d66b-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="7d66b-120">Özellik Ekle `Let` ve özellik `Get` özellik yordamları:</span><span class="sxs-lookup"><span data-stu-id="7d66b-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="7d66b-121">Bir işlevi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7d66b-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="7d66b-122">Oluşturma ve COM nesnesi tıklayarak kaydetme **olun ComObject1.dll** üzerinde **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7d66b-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d66b-123">Ayrıca bir COM nesnesi olarak Visual Basic ile oluşturulan bir sınıf getirebilir olsa da, doğru bir COM nesnesi değil ve bu izlenecek yolda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d66b-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="7d66b-124">Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7d66b-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="7d66b-125">Birlikte çalışma derlemeleri</span><span class="sxs-lookup"><span data-stu-id="7d66b-125">Interop Assemblies</span></span>  
 <span data-ttu-id="7d66b-126">Aşağıdaki yordamda, yönetilmeyen kod (örneğin, bir COM nesnesi) ve Visual Studio kullanan yönetilen kodu arasında bir köprü görevi gören bir birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d66b-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="7d66b-127">Visual Basic oluşturur birlikte çalışma derlemesi çoğu, gibi COM nesneleri ile çalışma ayrıntılarını işler *birlikte çalışma hazırlama*, işlem paketleme parametrelerinin ve dönüş değerlerine eşdeğeri veri türleri için geçerken ve COM nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7d66b-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="7d66b-128">Visual Basic uygulama başvurusu değil gerçek COM nesnesi birlikte çalışma derlemesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7d66b-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="7d66b-129">Bir COM nesnesi Visual Basic 2005 ve sonraki sürümler ile kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7d66b-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="7d66b-130">Yeni bir Visual Basic Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="7d66b-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="7d66b-131">Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="7d66b-132">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="7d66b-133">Üzerinde **COM** sekmesinde, çift `ComObject1` içinde **bileşen adı** listelemek ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="7d66b-134">Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="7d66b-135">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="7d66b-136">İçinde **şablonları** bölmesinde tıklayın **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="7d66b-137">Varsayılan dosya adı `Class1.vb`, görünür **adı** alan.</span><span class="sxs-lookup"><span data-stu-id="7d66b-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="7d66b-138">Bu alan MathClass.vb ve seçeneğini değiştirme **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7d66b-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="7d66b-139">Bu adlı bir sınıf oluşturur `MathClass`ve kendi kodunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7d66b-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="7d66b-140">Üstüne aşağıdaki kodu ekleyin `MathClass` COM sınıfından devralmak için.</span><span class="sxs-lookup"><span data-stu-id="7d66b-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7.  <span data-ttu-id="7d66b-141">Aşağıdaki kodu ekleyerek temel sınıfının ortak yöntemi aşırı `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="7d66b-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8.  <span data-ttu-id="7d66b-142">Aşağıdaki kodu ekleyerek devralınan sınıf genişletmek `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="7d66b-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 <span data-ttu-id="7d66b-143">Yeni bir sınıf COM nesnesi içinde temel sınıfın özelliklerini devralır, bir yöntem yüklemeleri ve sınıf genişletmek için yeni bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d66b-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="7d66b-144">Devralınan sınıf test etmek için</span><span class="sxs-lookup"><span data-stu-id="7d66b-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="7d66b-145">Başlangıç formunuza bir düğme ekleyin ve ardından kendi kodunu görüntülemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7d66b-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="7d66b-146">Düğmenin içinde `Click` olay işleyici yordamı, bir örneğini oluşturmak için aşağıdaki kodu ekleyin `MathClass` ve aşırı yüklenmiş yöntemler çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d66b-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3.  <span data-ttu-id="7d66b-147">F5 tuşuna basarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d66b-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="7d66b-148">Formunda, düğmeyi tıklattığınızda `AddNumbers` yöntemi ile ilk kez çağrıldığında `Short` sayı veri türü ve Visual Basic, temel sınıftan uygun yöntemi seçer.</span><span class="sxs-lookup"><span data-stu-id="7d66b-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="7d66b-149">İçin yapılan ikinci çağrı `AddNumbers` aşırı yükleme yöntemini yönlendirildiği `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="7d66b-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="7d66b-150">Üçüncü çağrı çağrıları `SubtractNumbers` sınıfını genişleten bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="7d66b-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="7d66b-151">Temel sınıf özelliği ayarlanmış ve değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7d66b-152">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="7d66b-152">Next Steps</span></span>  
 <span data-ttu-id="7d66b-153">Fark etmiş Aşırı yüklenen `AddNumbers` işlevi aynı veri COM nesnesinin temel sınıftan devralınan yöntemi olarak türüne sahip görünür.</span><span class="sxs-lookup"><span data-stu-id="7d66b-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="7d66b-154">Temel sınıf yönteminin parametreleri ve bağımsız değişkenler, Visual Basic 6.0 16-bit tamsayılar olarak tanımlanır, ancak 16-bit tamsayı türü olarak kullanıma sunulur çünkü `Short` Visual Basic'in daha sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="7d66b-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="7d66b-155">Yeni işlev 32-bit tamsayı kabul eder ve temel sınıf işlev aşırı.</span><span class="sxs-lookup"><span data-stu-id="7d66b-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="7d66b-156">COM nesneleriyle çalışırken, parametre boyutunu ve veri türlerini doğruladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7d66b-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="7d66b-157">Örneğin, bir Visual Basic 6.0 koleksiyon nesnesi bağımsız değişken olarak kabul eden bir COM nesnesi kullandığınızda, Visual Basic'in sonraki bir sürümünü koleksiyonundan sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="7d66b-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="7d66b-158">Özellikler ve yöntemler COM sınıflardan devralınan bir yerel özellik veya değiştiren bir özellik veya temel bir COM sınıftan devralınan yöntemini bildirebilirsiniz anlamı kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="7d66b-159">Devralınan COM özellikleri geçersiz kılmak için kuralları, diğer özellikleri ve yöntemleri aşağıdaki istisnalar dışında geçersiz kılmak için kurallar benzerdir:</span><span class="sxs-lookup"><span data-stu-id="7d66b-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="7d66b-160">Herhangi bir özelliği veya bir COM sınıftan devralınan yöntemi geçersiz kılarsanız, tüm diğer devralınan özellikleri ve yöntemleri geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d66b-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="7d66b-161">Kullandığınız özellikler `ByRef` parametreleri geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="7d66b-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d66b-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d66b-162">See also</span></span>
- [<span data-ttu-id="7d66b-163">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="7d66b-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="7d66b-164">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="7d66b-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="7d66b-165">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7d66b-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
