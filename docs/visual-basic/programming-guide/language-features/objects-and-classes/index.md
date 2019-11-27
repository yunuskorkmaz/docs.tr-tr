---
title: Nesneler ve sınıflar
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: d45aca8b137f56cf058b63b9286504259c0005eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346699"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="2b5bc-102">Visual Basic içindeki nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="2b5bc-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="2b5bc-103">Bir *nesne* , bir birim olarak kabul edilebilir kod ve verilerin bir birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="2b5bc-104">Bir nesne, bir denetim veya form gibi bir uygulamanın parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="2b5bc-105">Tüm uygulama da bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-105">An entire application can also be an object.</span></span>

<span data-ttu-id="2b5bc-106">Visual Basic bir uygulama oluşturduğunuzda, sürekli olarak nesnelerle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="2b5bc-107">Denetim, form ve veri erişim nesneleri gibi Visual Basic tarafından sunulan nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="2b5bc-108">Ayrıca, Visual Basic uygulamanızdaki diğer uygulamalardan da nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="2b5bc-109">Hatta kendi nesnelerinizi oluşturabilir ve bunlara yönelik ek özellikler ve Yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="2b5bc-110">Nesneler, programlar için önceden yazılmış derleme blokları gibi davranır; bir kez kod parçası yazmanızı ve üzerinde ve üzerinde yeniden kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="2b5bc-111">Bu konu, nesneleri ayrıntılı bir şekilde ele alır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="2b5bc-112">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="2b5bc-112">Objects and classes</span></span>

<span data-ttu-id="2b5bc-113">Visual Basic içindeki her nesne bir *sınıf*tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="2b5bc-114">Bir sınıf, bir nesnenin değişkenlerini, özelliklerini, yordamlarını ve olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="2b5bc-115">Nesneler sınıfların örnekleridir; bir sınıfı tanımladıktan sonra ihtiyacınız olan sayıda nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="2b5bc-116">Bir nesne ve sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgilerini düşünün.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="2b5bc-117">Tanımlama bilgisi kesici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-117">The cookie cutter is the class.</span></span> <span data-ttu-id="2b5bc-118">Her tanımlama bilgisinin, örneğin boyut ve şekil özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="2b5bc-119">Sınıfı, nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-119">The class is used to create objects.</span></span> <span data-ttu-id="2b5bc-120">Nesneler tanımlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-120">The objects are the cookies.</span></span>

<span data-ttu-id="2b5bc-121">Üyelerine erişebilmek için önce bir nesnesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-121">You must create an object before you can access its members.</span></span>

### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="2b5bc-122">Bir sınıftan bir nesne oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2b5bc-122">To create an object from a class</span></span>

1. <span data-ttu-id="2b5bc-123">Hangi sınıftan bir nesne oluşturmak istediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-123">Determine from which class you want to create an object.</span></span>

2. <span data-ttu-id="2b5bc-124">Bir sınıf örneği atayabilmeniz için bir değişken oluşturmak üzere bir [Dim bildirisi](../../../../visual-basic/language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="2b5bc-125">Değişken, istenen sınıfın türünden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="2b5bc-126">Değişkeni sınıfının yeni bir örneğine başlatmak için [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="2b5bc-127">Artık nesne değişkeni aracılığıyla sınıfın üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-127">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="2b5bc-128">Mümkün olduğunda, değişkeni atamak istediğiniz sınıf türünde olacak şekilde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="2b5bc-129">Bu, *erken bağlama*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-129">This is called *early binding*.</span></span> <span data-ttu-id="2b5bc-130">Derleme zamanında sınıf türünü bilmiyorsanız, değişkeni [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak şekilde bildirerek *geç bağlamayı* çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="2b5bc-131">Ancak, geç bağlama performansı daha yavaş yapabilir ve çalışma zamanı nesnesinin üyelerine erişimi sınırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="2b5bc-132">Daha fazla bilgi için bkz. [nesne değişkeni bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="2b5bc-133">Birden çok örnek</span><span class="sxs-lookup"><span data-stu-id="2b5bc-133">Multiple instances</span></span>

<span data-ttu-id="2b5bc-134">Bir sınıftan yeni oluşturulan nesneler genellikle birbirleriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="2b5bc-135">Ancak, ayrı nesneler olarak varolduktan sonra, değişkenleri ve özellikleri diğer örneklerden bağımsız olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="2b5bc-136">Örneğin, bir forma üç onay kutusu eklerseniz, her onay kutusu nesnesi <xref:System.Windows.Forms.CheckBox> sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="2b5bc-137">Bireysel <xref:System.Windows.Forms.CheckBox> nesneleri, sınıf tarafından tanımlanan ortak bir özellik ve özellik kümesini (özellikler, değişkenler, yordamlar ve olaylar) paylaşır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="2b5bc-138">Ancak, her birinin kendi adı vardır, bağımsız olarak etkinleştirilebilir ve devre dışı bırakılabilir ve formda farklı bir konuma yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="2b5bc-139">Nesne üyeleri</span><span class="sxs-lookup"><span data-stu-id="2b5bc-139">Object members</span></span>

<span data-ttu-id="2b5bc-140">Bir nesne, bir sınıfın *örneğini* temsil eden bir uygulamanın öğesidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="2b5bc-141">Alanlar, özellikler, Yöntemler ve olaylar, nesnelerin yapı taşlarıdır ve *üyelerini*oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="2b5bc-142">Üye Erişimi</span><span class="sxs-lookup"><span data-stu-id="2b5bc-142">Member Access</span></span>

<span data-ttu-id="2b5bc-143">Bir nesnenin üyesine, nesne değişkeninin adını, bir nokta (`.`) ve üyenin adını belirterek erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="2b5bc-144">Aşağıdaki örnek, bir <xref:System.Windows.Forms.Label> nesnesinin <xref:System.Windows.Forms.Control.Text%2A> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="2b5bc-145">Üyelerin IntelliSense listesi</span><span class="sxs-lookup"><span data-stu-id="2b5bc-145">IntelliSense listing of members</span></span>

<span data-ttu-id="2b5bc-146">IntelliSense, liste üyeleri seçeneğini çağırdığınızda bir sınıfın üyelerini listeler, örneğin, üye erişim işleci olarak bir nokta (`.`) yazdığınızda.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="2b5bc-147">Bu sınıfın bir örneği olarak belirtilen değişkenin adını izleyen bir süre yazarsanız, IntelliSense tüm örnek üyelerini ve paylaşılan üyelerin hiçbirini listeler.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="2b5bc-148">Sınıf adının kendisini izleyen dönemi yazarsanız, IntelliSense tüm paylaşılan üyeleri ve örnek üyelerinden hiçbirini listeler.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="2b5bc-149">Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="2b5bc-150">Alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="2b5bc-150">Fields and properties</span></span>

<span data-ttu-id="2b5bc-151">*Alanlar* ve *Özellikler* bir nesnesinde depolanan bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="2b5bc-152">Değerlerini atama deyimleriyle alır ve bir yordamda yerel değişkenleri ayarladığınız şekilde ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="2b5bc-153">Aşağıdaki örnek <xref:System.Windows.Forms.Control.Width%2A> özelliğini alır ve bir <xref:System.Windows.Forms.Label> nesnesinin <xref:System.Windows.Forms.Control.ForeColor%2A> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="2b5bc-154">Bir alana *üye değişkeni*olarak da adlandırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-154">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="2b5bc-155">Şu durumlarda özellik yordamlarını kullan:</span><span class="sxs-lookup"><span data-stu-id="2b5bc-155">Use property procedures when:</span></span>

- <span data-ttu-id="2b5bc-156">Değerin ne zaman ve nasıl ayarlanacağını veya alındığını kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="2b5bc-157">Özelliğin doğrulanması gereken, iyi tanımlanmış bir değer kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="2b5bc-158">Değerin ayarlanması, nesnenin durumunda bir `IsVisible` özelliği gibi bazı algılanabilir değişmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="2b5bc-159">Özelliği ayarlamak, diğer iç değişkenlerde veya diğer özelliklerin değerlerine değişikliklere neden olur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="2b5bc-160">Özelliğin ayarlanamayacağını veya alınabilmesi için önce bir adım kümesi gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="2b5bc-161">Şu durumlarda alanları kullan:</span><span class="sxs-lookup"><span data-stu-id="2b5bc-161">Use fields when:</span></span>

- <span data-ttu-id="2b5bc-162">Değer kendi kendine doğrulama türüdür.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-162">The value is of a self-validating type.</span></span> <span data-ttu-id="2b5bc-163">Örneğin, bir `Boolean` değişkenine `True` veya `False` dışında bir değer atanırsa bir hata veya otomatik veri dönüştürme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="2b5bc-164">Veri türü tarafından desteklenen aralıktaki herhangi bir değer geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="2b5bc-165">Bu, `Single` veya `Double`türündeki birçok özellik için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="2b5bc-166">Özelliği bir `String` veri türüdür ve dizenin boyutu veya değerinde bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="2b5bc-167">Daha fazla bilgi için bkz. [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="2b5bc-168">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2b5bc-168">Methods</span></span>

<span data-ttu-id="2b5bc-169">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="2b5bc-170">Örneğin <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, bir açılan kutuya yeni bir giriş ekleyen <xref:System.Windows.Forms.ComboBox> nesnesinin bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="2b5bc-171">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.Timer> nesnesinin <xref:System.Windows.Forms.Timer.Start%2A> yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="2b5bc-172">Bir yöntemin yalnızca bir nesne tarafından sunulan bir *yordam* olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="2b5bc-173">Daha fazla bilgi için bkz. [yordamlar](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="2b5bc-174">Olaylar</span><span class="sxs-lookup"><span data-stu-id="2b5bc-174">Events</span></span>

<span data-ttu-id="2b5bc-175">Bir olay, fareyi tıklatmak veya bir tuşa basmak ve yanıt vermek için kod yazabileceğiniz gibi bir nesne tarafından tanınan bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="2b5bc-176">Olaylar, bir kullanıcı eylemi veya program kodu sonucu olarak veya sistem tarafından neden olabileceği için oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="2b5bc-177">Bir olaya işaret eden kod, olayı *yükseltmek* ve kendisine yanıt veren kod onu *işleyecek* şekilde söylenir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="2b5bc-178">Ayrıca, kendi özel olaylarınızı kendi nesneleriniz tarafından da geliştirebilirsiniz ve diğer nesneler tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="2b5bc-179">Daha fazla bilgi için bkz. [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="2b5bc-180">Örnek üyeleri ve paylaşılan Üyeler</span><span class="sxs-lookup"><span data-stu-id="2b5bc-180">Instance members and shared members</span></span>

<span data-ttu-id="2b5bc-181">Bir sınıftan bir nesne oluşturduğunuzda, sonuç bu sınıfın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="2b5bc-182">[Paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) anahtar sözcükle bildirilmeyen Üyeler *örnek üyeleridir*ve bu belirli örneğe tamamen aittir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="2b5bc-183">Bir örnekteki örnek üye, aynı sınıfın başka bir örneğindeki aynı Üyeden bağımsız.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="2b5bc-184">Örneğin, örnek üye değişkeni farklı örneklerde farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="2b5bc-185">`Shared` anahtar sözcüğüyle belirtilen Üyeler, belirli bir örneğe değil, bir bütün olarak sınıfa ait olan *paylaşılan üyeleridir*.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="2b5bc-186">Paylaşılan bir üye yalnızca bir kez bulunur, sınıfının kaç örneği oluşturabileceğiniz ve hatta örnek oluştursanız bile.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="2b5bc-187">Örneğin, bir paylaşılan üye değişkeni, sınıfına erişebilen tüm kodlar için kullanılabilen yalnızca bir değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="2b5bc-188">Paylaşılmayan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="2b5bc-188">Accessing nonshared members</span></span>

##### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="2b5bc-189">Bir nesnenin paylaşılmayan üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="2b5bc-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="2b5bc-190">Nesnesinin sınıfından oluşturulduğundan ve bir nesne değişkenine atandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="2b5bc-191">Üyeye erişen ifadede, nesne değişkeni adını *üye erişim işleci* (`.`) ve ardından üye adı ile birlikte izleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="2b5bc-192">Paylaşılan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="2b5bc-192">Accessing shared members</span></span>

##### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="2b5bc-193">Bir nesnenin paylaşılan üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="2b5bc-193">To access a shared member of an object</span></span>

- <span data-ttu-id="2b5bc-194">*Üye erişim işleci* (`.`) ve ardından üye adı ile sınıf adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="2b5bc-195">Nesnenin `Shared` üyesine her zaman doğrudan sınıf adı aracılığıyla erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="2b5bc-196">Sınıfından zaten bir nesne oluşturduysanız, nesne değişkeni aracılığıyla bir `Shared` üyeye erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="2b5bc-197">Sınıflar ve modüller arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="2b5bc-197">Differences between classes and modules</span></span>

<span data-ttu-id="2b5bc-198">Sınıflar ve modüller arasındaki temel fark, sınıfların standart modüller kullanılamadığı sürece nesneler olarak örneklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="2b5bc-199">Standart modülün verilerinin yalnızca bir kopyası olduğundan, programınızın bir kısmı standart bir modülde ortak bir değişkeni değiştirdiğinde, programın başka bir kısmı o değişkeni okuduğunda aynı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="2b5bc-200">Buna karşılık, nesne verileri her bir örneklenmiş nesne için ayrı olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="2b5bc-201">Diğer bir farklılık ise standart modüllerin aksine sınıfların arabirimler uygulayabildiği bir farktır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="2b5bc-202">`Shared` değiştiricisi bir sınıf üyesine uygulandığında, sınıfının belirli bir örneği yerine sınıfın kendisiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="2b5bc-203">Üyeye doğrudan sınıf adı kullanılarak erişilir, modül üyelerine aynı şekilde erişilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="2b5bc-204">Sınıflar ve modüller, üyeleri için farklı kapsamlar da kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="2b5bc-205">Bir sınıf içinde tanımlanan Üyeler, sınıfın belirli bir örneği içinde kapsamlandırılır ve yalnızca nesnenin ömrü için mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="2b5bc-206">Sınıf üyelerine bir sınıfın dışından erişmek için, *nesne*biçiminde tam nitelikli adlar kullanmanız gerekir. *Üye*.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="2b5bc-207">Öte yandan, bir modül içinde bildirilen üyelere varsayılan olarak genel olarak erişilebilir ve modüle erişebilen herhangi bir kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="2b5bc-208">Bu, bir standart modüldeki değişkenlerin, projenizdeki herhangi bir yerden görünedikleri ve programın ömrü için mevcut olduğu için etkin olmayan genel değişkenler olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="2b5bc-209">Sınıfları ve nesneleri yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="2b5bc-209">Reusing classes and objects</span></span>

<span data-ttu-id="2b5bc-210">Nesneler, değişkenleri ve yordamları bir kez bildirmenizi ve sonra gerektiğinde bunları yeniden kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="2b5bc-211">Örneğin, bir uygulamaya yazım denetleyicisi eklemek istiyorsanız, yazım denetimi işlevselliği sağlamak için tüm değişkenleri ve destek işlevlerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="2b5bc-212">Yazım denetimcisini bir sınıf olarak oluşturursanız, derlenen derlemeye bir başvuru ekleyerek diğer uygulamalarda onu yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="2b5bc-213">Daha iyi bir şekilde, başka birinin zaten geliştirildiği bir yazım denetleyicisi sınıfını kullanarak kendi çalışmalarınızı kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="2b5bc-214">.NET Framework, kullanılabilir bileşenlere birçok örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-214">The .NET Framework provides many examples of components that are available for use.</span></span> <span data-ttu-id="2b5bc-215">Aşağıdaki örnek, <xref:System> ad alanındaki <xref:System.TimeZone> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="2b5bc-216"><xref:System.TimeZone>, geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza izin veren Üyeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub examineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    MsgBox(s)
End Sub
```

<span data-ttu-id="2b5bc-217">Önceki örnekte, ilk [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md) <xref:System.TimeZone> türünde bir nesne değişkeni bildirilir ve <xref:System.TimeZone.CurrentTimeZone%2A> özelliği tarafından döndürülen <xref:System.TimeZone> nesnesine atanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="2b5bc-218">Nesneler arasındaki ilişkiler</span><span class="sxs-lookup"><span data-stu-id="2b5bc-218">Relationships among objects</span></span>

<span data-ttu-id="2b5bc-219">Nesneler birbirleriyle çeşitli yollarla ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="2b5bc-220">Asıl ilişki türleri *hiyerarşik* ve *kapsamlardır*.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="2b5bc-221">Hiyerarşik ilişki</span><span class="sxs-lookup"><span data-stu-id="2b5bc-221">Hierarchical relationship</span></span>

<span data-ttu-id="2b5bc-222">Sınıflar daha temel sınıflardan türetildiklerinde *hiyerarşik bir ilişkiye*sahip oldukları söylenir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="2b5bc-223">Sınıf hiyerarşileri, daha genel bir sınıfın alt türü olan öğeleri açıklayarak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="2b5bc-224">Aşağıdaki örnekte, normal <xref:System.Windows.Forms.Button> gibi davranan ve ayrıca ön plan ve arka plan renklerini tersine getiren bir yöntemi gösteren özel bir <xref:System.Windows.Forms.Button> türünü tanımlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="2b5bc-225">Bir sınıf tanımlamak için zaten var olan bir sınıftan türetilmiş</span><span class="sxs-lookup"><span data-stu-id="2b5bc-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="2b5bc-226">İhtiyaç duyduğunuz nesnenin oluşturulacağı bir sınıf tanımlamak için bir [Class ifadesini](../../../../visual-basic/language-reference/statements/class-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="2b5bc-227">`End Class` deyimin sınıfınızın son kod satırını izlediği emin olun.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="2b5bc-228">Varsayılan olarak, tümleşik geliştirme ortamı (IDE), bir `Class` bildiriminde girdiğinizde otomatik olarak bir `End Class` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="2b5bc-229">[Inherits ifadesiyle](../../../../visual-basic/language-reference/statements/inherits-statement.md)hemen `Class` ifadesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="2b5bc-230">Yeni sınıfınızın türetildiği sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-230">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="2b5bc-231">Yeni sınıfınız, temel sınıf tarafından tanımlanan tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="2b5bc-232">Türetilmiş sınıfınızın sunduğu ek Üyeler için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="2b5bc-233">Örneğin, bir `reverseColors` yöntemi ekleyebilirsiniz ve türetilmiş sınıfınız aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="2b5bc-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class reversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub reverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="2b5bc-234">`reversibleButton` sınıfından bir nesne oluşturursanız, bu, <xref:System.Windows.Forms.Button> sınıfının tüm üyelerine, ayrıca `reverseColors` yöntemi ve `reversibleButton`üzerinde tanımladığınız diğer yeni üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="2b5bc-235">Türetilmiş sınıflar, bir sınıf hiyerarşisinde ilerlemeniz sırasında karmaşıklık eklemenize olanak sağlayan, temel alınan sınıftan üyeleri devralınır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="2b5bc-236">Daha fazla bilgi için bkz. [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

### <a name="compiling-the-code"></a><span data-ttu-id="2b5bc-237">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="2b5bc-237">Compiling the code</span></span>

<span data-ttu-id="2b5bc-238">Derleyicinin yeni sınıfınızı türettiğiniz sınıfa erişip erişemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="2b5bc-239">Bu, önceki örnekte olduğu gibi adını tam olarak niteleyen veya [Imports ifadesinde (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ad alanını tanımlayan anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="2b5bc-240">Sınıf farklı bir projem ise, bu projeye bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="2b5bc-241">Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="2b5bc-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="2b5bc-242">Kapsama ilişkisi</span><span class="sxs-lookup"><span data-stu-id="2b5bc-242">Containment relationship</span></span>

<span data-ttu-id="2b5bc-243">Nesnelerin ilişkili olduğu başka bir yol da *kapsama ilişkisidir*.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="2b5bc-244">Kapsayıcı nesneleri diğer nesneleri mantıksal olarak kapsüllendirir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="2b5bc-245">Örneğin, <xref:System.OperatingSystem> nesnesi mantıksal olarak <xref:System.OperatingSystem.Version%2A> özelliğini döndüren bir <xref:System.Version> nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="2b5bc-246">Kapsayıcı nesnesinin fiziksel olarak başka bir nesne içermediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="2b5bc-247">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="2b5bc-247">Collections</span></span>

<span data-ttu-id="2b5bc-248">Nesne *kapsamaların*belirli bir türü koleksiyonlar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="2b5bc-249">Koleksiyonlar, numaralandırılabilir benzer nesne gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="2b5bc-250">Visual Basic her biri Için içindeki belirli bir sözdizimini destekler [... ](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)Bir koleksiyonun öğeleri arasında yineleme yapmanızı sağlayan Next bildirisi.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="2b5bc-251">Ayrıca, Koleksiyonlar genellikle öğeleri dizine göre almak veya benzersiz bir dizeyle ilişkilendirerek bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="2b5bc-252">Koleksiyonlar, dizinleri kullanmadan öğeleri eklemenize veya kaldırmanıza izin verdiklerinden, dizilerden kullanımı daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="2b5bc-253">Kullanım kolaylığı nedeniyle, Koleksiyonlar genellikle formları ve denetimleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="2b5bc-254">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="2b5bc-254">Related topics</span></span>

<span data-ttu-id="2b5bc-255">[Izlenecek yol: sınıfları tanımlama](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="2b5bc-256">Sınıfının nasıl oluşturulacağı hakkında adım adım bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-256">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="2b5bc-257">[Aşırı yüklenmiş Özellikler ve yöntemler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="2b5bc-258">Aşırı Yüklenmiş Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2b5bc-258">Overloaded Properties and Methods</span></span>

<span data-ttu-id="2b5bc-259">[Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>\
<span data-ttu-id="2b5bc-260">Devralma değiştiricilerini, yöntemleri ve özellikleri geçersiz kılmayı, MyClass ve MyBase 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="2b5bc-261">[Nesne ömrü: nesneleri oluşturma ve yok etme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="2b5bc-262">Sınıf örneklerinin oluşturulmasını ve elden atılanışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-262">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="2b5bc-263">[Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>\
<span data-ttu-id="2b5bc-264">Veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanıza izin veren anonim türlerin nasıl oluşturulduğunu ve kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="2b5bc-265">[Nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="2b5bc-266">Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="2b5bc-267">[Nasıl yapılır: anonim tür bildirimlerinde özellik adlarını ve türleri çıkarçıkar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="2b5bc-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="2b5bc-268">Anonim tür bildirimlerinde özellik adlarının ve türlerin nasıl çıkarılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="2b5bc-269">Başarılı ve başarısız çıkarım örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5bc-269">Provides examples of successful and unsuccessful inference.</span></span>
