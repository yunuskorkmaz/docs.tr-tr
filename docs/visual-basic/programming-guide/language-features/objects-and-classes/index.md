---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic nesneler ve sınıflar'
title: Nesneler ve sınıflar
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9cefcc117c9dd4ac42940f342dbf75d8ddb4f41d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462730"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="a1ded-103">Visual Basic içindeki nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a1ded-103">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="a1ded-104">Bir *nesne* , bir birim olarak kabul edilebilir kod ve verilerin bir birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-104">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="a1ded-105">Bir nesne, bir denetim veya form gibi bir uygulamanın parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-105">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="a1ded-106">Tüm uygulama da bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-106">An entire application can also be an object.</span></span>

<span data-ttu-id="a1ded-107">Visual Basic bir uygulama oluşturduğunuzda, sürekli olarak nesnelerle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="a1ded-107">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="a1ded-108">Denetim, form ve veri erişim nesneleri gibi Visual Basic tarafından sunulan nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-108">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="a1ded-109">Ayrıca, Visual Basic uygulamanızdaki diğer uygulamalardan da nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-109">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="a1ded-110">Hatta kendi nesnelerinizi oluşturabilir ve bunlara yönelik ek özellikler ve Yöntemler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-110">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="a1ded-111">Nesneler, programlar için önceden yazılmış derleme blokları gibi davranır; bir kez kod parçası yazmanızı ve üzerinde ve üzerinde yeniden kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-111">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="a1ded-112">Bu konu, nesneleri ayrıntılı bir şekilde ele alır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-112">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="a1ded-113">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a1ded-113">Objects and classes</span></span>

<span data-ttu-id="a1ded-114">Visual Basic içindeki her nesne bir *sınıf* tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-114">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="a1ded-115">Bir sınıf, bir nesnenin değişkenlerini, özelliklerini, yordamlarını ve olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-115">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="a1ded-116">Nesneler sınıfların örnekleridir; bir sınıfı tanımladıktan sonra ihtiyacınız olan sayıda nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-116">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="a1ded-117">Bir nesne ve sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgilerini düşünün.</span><span class="sxs-lookup"><span data-stu-id="a1ded-117">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="a1ded-118">Tanımlama bilgisi kesici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-118">The cookie cutter is the class.</span></span> <span data-ttu-id="a1ded-119">Her tanımlama bilgisinin, örneğin boyut ve şekil özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-119">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="a1ded-120">Sınıfı, nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-120">The class is used to create objects.</span></span> <span data-ttu-id="a1ded-121">Nesneler tanımlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="a1ded-121">The objects are the cookies.</span></span>

<span data-ttu-id="a1ded-122">Bir nesnesi, [`Shared`](../../../language-reference/modifiers/shared.md) sınıfının bir nesnesi olmadan erişilebilen Üyeler hariç, üyelerine erişebilmek için önce bir nesne oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-122">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="a1ded-123">Sınıftan nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1ded-123">Create an object from a class</span></span>

1. <span data-ttu-id="a1ded-124">Hangi sınıftan bir nesne oluşturmak istediğinizi belirleyin veya kendi sınıfınızı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-124">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="a1ded-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a1ded-125">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="a1ded-126">Bir sınıf örneği atayabilmeniz için bir değişken oluşturmak üzere bir [Dim bildirisi](../../../language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-126">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="a1ded-127">Değişken, istenen sınıfın türünden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-127">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="a1ded-128">Değişkeni sınıfının yeni bir örneğine başlatmak için [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-128">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="a1ded-129">Artık nesne değişkeni aracılığıyla sınıfın üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-129">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="a1ded-130">Mümkün olduğunda, değişkeni atamak istediğiniz sınıf türünde olacak şekilde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-130">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="a1ded-131">Bu, *erken bağlama* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-131">This is called *early binding*.</span></span> <span data-ttu-id="a1ded-132">Derleme zamanında sınıf türünü bilmiyorsanız, değişkeni [nesne veri türünde](../../../language-reference/data-types/object-data-type.md)olacak şekilde bildirerek *geç bağlamayı* çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-132">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="a1ded-133">Ancak, geç bağlama performansı daha yavaş yapabilir ve çalışma zamanı nesnesinin üyelerine erişimi sınırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-133">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="a1ded-134">Daha fazla bilgi için bkz. [nesne değişkeni bildirimi](../variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a1ded-134">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="a1ded-135">Birden çok örnek</span><span class="sxs-lookup"><span data-stu-id="a1ded-135">Multiple instances</span></span>

<span data-ttu-id="a1ded-136">Bir sınıftan yeni oluşturulan nesneler genellikle birbirleriyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-136">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="a1ded-137">Ancak, ayrı nesneler olarak varolduktan sonra, değişkenleri ve özellikleri diğer örneklerden bağımsız olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-137">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="a1ded-138">Örneğin, bir forma üç onay kutusu eklerseniz, her onay kutusu nesnesi sınıfının bir örneğidir <xref:System.Windows.Forms.CheckBox> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-138">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="a1ded-139">Ayrı <xref:System.Windows.Forms.CheckBox> nesneler, sınıf tarafından tanımlanan ortak bir özellik ve özellik kümesini (özellikler, değişkenler, yordamlar ve olaylar) paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-139">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="a1ded-140">Ancak, her birinin kendi adı vardır, bağımsız olarak etkinleştirilebilir ve devre dışı bırakılabilir ve formda farklı bir konuma yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-140">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="a1ded-141">Nesne üyeleri</span><span class="sxs-lookup"><span data-stu-id="a1ded-141">Object members</span></span>

<span data-ttu-id="a1ded-142">Bir nesne, bir sınıfın *örneğini* temsil eden bir uygulamanın öğesidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-142">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="a1ded-143">Alanlar, özellikler, Yöntemler ve olaylar, nesnelerin yapı taşlarıdır ve *üyelerini* oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1ded-143">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="a1ded-144">Üye Erişimi</span><span class="sxs-lookup"><span data-stu-id="a1ded-144">Member Access</span></span>

<span data-ttu-id="a1ded-145">Bir nesnenin üyesine, nesne değişkeninin adını, bir nokta ( `.` ) ve üyenin adını belirterek erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-145">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="a1ded-146">Aşağıdaki örnek <xref:System.Windows.Forms.Control.Text%2A> bir nesnesinin özelliğini ayarlar <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-146">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="a1ded-147">Üyelerin IntelliSense listesi</span><span class="sxs-lookup"><span data-stu-id="a1ded-147">IntelliSense listing of members</span></span>

<span data-ttu-id="a1ded-148">IntelliSense, liste üyeleri seçeneğini çağırdığınızda bir sınıfın üyelerini listeler, örneğin, `.` üye erişim operatörü olarak bir nokta () yazdığınızda.</span><span class="sxs-lookup"><span data-stu-id="a1ded-148">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="a1ded-149">Bu sınıfın bir örneği olarak belirtilen değişkenin adını izleyen bir süre yazarsanız, IntelliSense tüm örnek üyelerini ve paylaşılan üyelerin hiçbirini listeler.</span><span class="sxs-lookup"><span data-stu-id="a1ded-149">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="a1ded-150">Sınıf adının kendisini izleyen dönemi yazarsanız, IntelliSense tüm paylaşılan üyeleri ve örnek üyelerinden hiçbirini listeler.</span><span class="sxs-lookup"><span data-stu-id="a1ded-150">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="a1ded-151">Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="a1ded-151">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="a1ded-152">Alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="a1ded-152">Fields and properties</span></span>

<span data-ttu-id="a1ded-153">*Alanlar* ve *Özellikler* bir nesnesinde depolanan bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1ded-153">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="a1ded-154">Değerlerini atama deyimleriyle alır ve bir yordamda yerel değişkenleri ayarladığınız şekilde ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a1ded-154">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="a1ded-155">Aşağıdaki örnek, özelliğini alır <xref:System.Windows.Forms.Control.Width%2A> ve <xref:System.Windows.Forms.Control.ForeColor%2A> bir nesnenin özelliğini ayarlar <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-155">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="a1ded-156">Bir alana *üye değişkeni* olarak da adlandırıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-156">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="a1ded-157">Şu durumlarda özellik yordamlarını kullan:</span><span class="sxs-lookup"><span data-stu-id="a1ded-157">Use property procedures when:</span></span>

- <span data-ttu-id="a1ded-158">Değerin ne zaman ve nasıl ayarlanacağını veya alındığını kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-158">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="a1ded-159">Özelliğin doğrulanması gereken, iyi tanımlanmış bir değer kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-159">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="a1ded-160">Değerin ayarlanması nesnenin durumunda bir özellik gibi bazı algılanabilir değişmesine neden olur `IsVisible` .</span><span class="sxs-lookup"><span data-stu-id="a1ded-160">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="a1ded-161">Özelliği ayarlamak, diğer iç değişkenlerde veya diğer özelliklerin değerlerine değişikliklere neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1ded-161">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="a1ded-162">Özelliğin ayarlanamayacağını veya alınabilmesi için önce bir adım kümesi gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-162">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="a1ded-163">Şu durumlarda alanları kullan:</span><span class="sxs-lookup"><span data-stu-id="a1ded-163">Use fields when:</span></span>

- <span data-ttu-id="a1ded-164">Değer kendi kendine doğrulama türüdür.</span><span class="sxs-lookup"><span data-stu-id="a1ded-164">The value is of a self-validating type.</span></span> <span data-ttu-id="a1ded-165">Örneğin, bir değişken ya da `True` `False` bir değişkene atanan bir değer varsa, bir hata veya otomatik veri dönüştürme gerçekleşir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="a1ded-165">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="a1ded-166">Veri türü tarafından desteklenen aralıktaki herhangi bir değer geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-166">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="a1ded-167">Bu, veya türündeki birçok özellik için geçerlidir `Single` `Double` .</span><span class="sxs-lookup"><span data-stu-id="a1ded-167">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="a1ded-168">Özelliği bir `String` veri türüdür ve dizenin boyutu veya değerinde bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1ded-168">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="a1ded-169">Daha fazla bilgi için bkz. [özellik yordamları](../procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a1ded-169">For more information, see [Property Procedures](../procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="a1ded-170">Her zaman sabit olmayan alanları özel tutun.</span><span class="sxs-lookup"><span data-stu-id="a1ded-170">Always keep the non-constant fields private.</span></span> <span data-ttu-id="a1ded-171">Ortak hale getirmek istediğinizde, bunun yerine bir özellik kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-171">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="a1ded-172">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a1ded-172">Methods</span></span>

<span data-ttu-id="a1ded-173">Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-173">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="a1ded-174">Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> <xref:System.Windows.Forms.ComboBox> bir Birleşik giriş kutusuna yeni bir giriş ekleyen nesnenin bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-174">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="a1ded-175">Aşağıdaki örnek <xref:System.Windows.Forms.Timer.Start%2A> bir nesnesinin yöntemini gösterir <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-175">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="a1ded-176">Bir yöntemin yalnızca bir nesne tarafından sunulan bir *yordam* olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-176">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="a1ded-177">Daha fazla bilgi için bkz. [yordamlar](../procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1ded-177">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="a1ded-178">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="a1ded-178">Events</span></span>

<span data-ttu-id="a1ded-179">Bir olay, fareyi tıklatmak veya bir tuşa basmak ve yanıt vermek için kod yazabileceğiniz gibi bir nesne tarafından tanınan bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-179">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="a1ded-180">Olaylar, bir kullanıcı eylemi veya program kodu sonucu olarak veya sistem tarafından neden olabileceği için oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-180">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="a1ded-181">Bir olaya işaret eden kod, olayı *yükseltmek* ve kendisine yanıt veren kod onu *işleyecek* şekilde söylenir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-181">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="a1ded-182">Ayrıca, kendi özel olaylarınızı kendi nesneleriniz tarafından da geliştirebilirsiniz ve diğer nesneler tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-182">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="a1ded-183">Daha fazla bilgi için bkz. [Olaylar](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1ded-183">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="a1ded-184">Örnek üyeleri ve paylaşılan Üyeler</span><span class="sxs-lookup"><span data-stu-id="a1ded-184">Instance members and shared members</span></span>

<span data-ttu-id="a1ded-185">Bir sınıftan bir nesne oluşturduğunuzda, sonuç bu sınıfın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-185">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="a1ded-186">[Paylaşılan](../../../language-reference/modifiers/shared.md) anahtar sözcükle bildirilmeyen Üyeler *örnek üyeleridir* ve bu belirli örneğe tamamen aittir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-186">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="a1ded-187">Bir örnekteki örnek üye, aynı sınıfın başka bir örneğindeki aynı Üyeden bağımsız.</span><span class="sxs-lookup"><span data-stu-id="a1ded-187">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="a1ded-188">Örneğin, örnek üye değişkeni farklı örneklerde farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-188">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="a1ded-189">Anahtar sözcüğüyle belirtilen Üyeler `Shared` , belirli bir örneğe değil, bir bütün olarak sınıfa ait olan *paylaşılan üyeleridir*.</span><span class="sxs-lookup"><span data-stu-id="a1ded-189">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="a1ded-190">Paylaşılan bir üye yalnızca bir kez bulunur, sınıfının kaç örneği oluşturabileceğiniz ve hatta örnek oluştursanız bile.</span><span class="sxs-lookup"><span data-stu-id="a1ded-190">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="a1ded-191">Örneğin, bir paylaşılan üye değişkeni, sınıfına erişebilen tüm kodlar için kullanılabilen yalnızca bir değere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-191">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="a1ded-192">Paylaşılan olmayan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="a1ded-192">Accessing non-shared members</span></span>

1. <span data-ttu-id="a1ded-193">Nesnesinin sınıfından oluşturulduğundan ve bir nesne değişkenine atandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a1ded-193">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="a1ded-194">Üyeye erişen ifadede, nesne değişkeni adını *üye erişim işleci* ( `.` ) ve ardından üye adı ile birlikte izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-194">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="a1ded-195">Paylaşılan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="a1ded-195">Accessing shared members</span></span>

- <span data-ttu-id="a1ded-196">*Üye erişim işleci* ( `.` ) ve ardından üye adı ile sınıf adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-196">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="a1ded-197">`Shared`Doğrudan sınıf adı aracılığıyla nesnenin üyesine her zaman erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-197">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="a1ded-198">Sınıfından zaten bir nesne oluşturduysanız, başka bir `Shared` üyeye de nesnenin değişkeni aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-198">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="a1ded-199">Sınıflar ve modüller arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="a1ded-199">Differences between classes and modules</span></span>

<span data-ttu-id="a1ded-200">Sınıflar ve modüller arasındaki temel fark, sınıfların standart modüller kullanılamadığı sürece nesneler olarak örneklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-200">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="a1ded-201">Standart modülün verilerinin yalnızca bir kopyası olduğundan, programınızın bir kısmı standart bir modülde ortak bir değişkeni değiştirdiğinde, programın başka bir kısmı o değişkeni okuduğunda aynı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-201">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="a1ded-202">Buna karşılık, nesne verileri her bir örneklenmiş nesne için ayrı olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a1ded-202">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="a1ded-203">Diğer bir farklılık ise standart modüllerin aksine sınıfların arabirimler uygulayabildiği bir farktır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-203">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="a1ded-204">Bir sınıf, [MustInherit](../../../language-reference/modifiers/mustinherit.md) değiştiricisi ile işaretlenmişse doğrudan başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-204">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="a1ded-205">Ancak, modüller devralınabileceğinden Devralındığı için bir modülden hala farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-205">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="a1ded-206">`Shared`Değiştirici bir sınıf üyesine uygulandığında, sınıfının belirli bir örneği yerine sınıfın kendisiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-206">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="a1ded-207">Üyeye doğrudan sınıf adı kullanılarak erişilir, modül üyelerine aynı şekilde erişilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-207">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="a1ded-208">Sınıflar ve modüller, üyeleri için farklı kapsamlar da kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-208">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="a1ded-209">Bir sınıf içinde tanımlanan Üyeler, sınıfın belirli bir örneği içinde kapsamlandırılır ve yalnızca nesnenin ömrü için mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a1ded-209">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="a1ded-210">Sınıf üyelerine bir sınıfın dışından erişmek için, *nesne* biçiminde tam nitelikli adlar kullanmanız gerekir. *Üye*.</span><span class="sxs-lookup"><span data-stu-id="a1ded-210">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="a1ded-211">Öte yandan, bir modül içinde bildirilen üyelere varsayılan olarak genel olarak erişilebilir ve modüle erişebilen herhangi bir kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-211">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="a1ded-212">Bu, bir standart modüldeki değişkenlerin, projenizdeki herhangi bir yerden görünedikleri ve programın ömrü için mevcut olduğu için etkin olmayan genel değişkenler olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-212">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="a1ded-213">Sınıfları ve nesneleri yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="a1ded-213">Reusing classes and objects</span></span>

<span data-ttu-id="a1ded-214">Nesneler, değişkenleri ve yordamları bir kez bildirmenizi ve sonra gerektiğinde bunları yeniden kullanmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-214">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="a1ded-215">Örneğin, bir uygulamaya yazım denetleyicisi eklemek istiyorsanız, yazım denetimi işlevselliği sağlamak için tüm değişkenleri ve destek işlevlerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-215">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="a1ded-216">Yazım denetimcisini bir sınıf olarak oluşturursanız, derlenen derlemeye bir başvuru ekleyerek diğer uygulamalarda onu yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-216">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="a1ded-217">Daha iyi bir şekilde, başka birinin zaten geliştirildiği bir yazım denetleyicisi sınıfını kullanarak kendi çalışmalarınızı kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1ded-217">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="a1ded-218">.NET, kullanıma açık olan bileşenlere birçok örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-218">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="a1ded-219">Aşağıdaki örnek, <xref:System.TimeZone> <xref:System> ad alanındaki sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-219">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="a1ded-220"><xref:System.TimeZone> geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza izin veren Üyeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-220"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="a1ded-221">Önceki örnekte, ilk [Dim ifadesinde](../../../language-reference/statements/dim-statement.md) , türünde bir nesne değişkeni <xref:System.TimeZone> bildirilir ve bu nesneye <xref:System.TimeZone> , özelliği tarafından döndürülen bir nesne atanır <xref:System.TimeZone.CurrentTimeZone%2A> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-221">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="a1ded-222">Nesneler arasındaki ilişkiler</span><span class="sxs-lookup"><span data-stu-id="a1ded-222">Relationships among objects</span></span>

<span data-ttu-id="a1ded-223">Nesneler birbirleriyle çeşitli yollarla ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-223">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="a1ded-224">Asıl ilişki türleri *hiyerarşik* ve *kapsamlardır*.</span><span class="sxs-lookup"><span data-stu-id="a1ded-224">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="a1ded-225">Hiyerarşik ilişki</span><span class="sxs-lookup"><span data-stu-id="a1ded-225">Hierarchical relationship</span></span>

<span data-ttu-id="a1ded-226">Sınıflar daha temel sınıflardan türetildiklerinde *hiyerarşik bir ilişkiye* sahip oldukları söylenir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-226">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="a1ded-227">Sınıf hiyerarşileri, daha genel bir sınıfın alt türü olan öğeleri açıklayarak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-227">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="a1ded-228">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> normal gibi davranan <xref:System.Windows.Forms.Button> ve ayrıca ön plan ve arka plan renklerini tersine getiren bir yöntemi ortaya çıkaran özel bir tür tanımlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a1ded-228">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="a1ded-229">Zaten var olan bir sınıftan türetilmiş bir sınıf tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a1ded-229">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="a1ded-230">İhtiyaç duyduğunuz nesnenin oluşturulacağı bir sınıf tanımlamak için bir [Class ifadesini](../../../language-reference/statements/class-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-230">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="a1ded-231">Bir `End Class` deyimin sınıfınıza ait son kod satırını takip ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a1ded-231">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="a1ded-232">Varsayılan olarak, tümleşik geliştirme ortamı (IDE) bir ifade girdiğinizde otomatik olarak bir üretir `End Class` `Class` .</span><span class="sxs-lookup"><span data-stu-id="a1ded-232">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="a1ded-233">`Class`Bir [Inherits ifadesiyle](../../../language-reference/statements/inherits-statement.md)ifadeyi hemen izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-233">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="a1ded-234">Yeni sınıfınızın türetildiği sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-234">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="a1ded-235">Yeni sınıfınız, temel sınıf tarafından tanımlanan tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-235">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="a1ded-236">Türetilmiş sınıfınızın sunduğu ek Üyeler için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1ded-236">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="a1ded-237">Örneğin, bir `ReverseColors` Yöntem ekleyebilirsiniz ve türetilmiş sınıfınız aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="a1ded-237">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="a1ded-238">Sınıfından bir nesne oluşturursanız `ReversibleButton` , sınıfın tüm üyelerine <xref:System.Windows.Forms.Button> ve ' `ReverseColors` de tanımladığınız diğer tüm yeni üyelere erişebilir `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="a1ded-238">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="a1ded-239">Türetilmiş sınıflar, bir sınıf hiyerarşisinde ilerlemeniz sırasında karmaşıklık eklemenize olanak sağlayan, temel alınan sınıftan üyeleri devralınır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-239">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="a1ded-240">Daha fazla bilgi için bkz. [Devralma Temelleri](inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a1ded-240">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="a1ded-241">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="a1ded-241">Compile the code</span></span>

<span data-ttu-id="a1ded-242">Derleyicinin yeni sınıfınızı türettiğiniz sınıfa erişip erişemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-242">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="a1ded-243">Bu, önceki örnekte olduğu gibi adını tam olarak niteleyen veya [Imports ifadesinde (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)ad alanını tanımlayan anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-243">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="a1ded-244">Sınıf farklı bir projem ise, bu projeye bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-244">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="a1ded-245">Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="a1ded-245">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="a1ded-246">Kapsama ilişkisi</span><span class="sxs-lookup"><span data-stu-id="a1ded-246">Containment relationship</span></span>

<span data-ttu-id="a1ded-247">Nesnelerin ilişkili olduğu başka bir yol da *kapsama ilişkisidir*.</span><span class="sxs-lookup"><span data-stu-id="a1ded-247">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="a1ded-248">Kapsayıcı nesneleri diğer nesneleri mantıksal olarak kapsüllendirir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-248">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="a1ded-249">Örneğin, <xref:System.OperatingSystem> nesnesi mantıksal <xref:System.Version> olarak kendi özelliği aracılığıyla döndürülen bir nesnesi içerir <xref:System.OperatingSystem.Version%2A> .</span><span class="sxs-lookup"><span data-stu-id="a1ded-249">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="a1ded-250">Kapsayıcı nesnesinin fiziksel olarak başka bir nesne içermediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1ded-250">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="a1ded-251">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="a1ded-251">Collections</span></span>

<span data-ttu-id="a1ded-252">Nesne *kapsamaların* belirli bir türü koleksiyonlar tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-252">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="a1ded-253">Koleksiyonlar, numaralandırılabilir benzer nesne gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-253">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="a1ded-254">Visual Basic her biri Için içindeki belirli bir sözdizimini destekler [... ](../../../language-reference/statements/for-each-next-statement.md) Bir koleksiyonun öğeleri arasında yineleme yapmanızı sağlayan Next bildirisi.</span><span class="sxs-lookup"><span data-stu-id="a1ded-254">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="a1ded-255">Ayrıca, Koleksiyonlar genellikle <xref:Microsoft.VisualBasic.Collection.Item%2A> öğelerini dizine göre almak için veya bunları benzersiz bir dizeyle ilişkilendirerek kullanmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-255">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="a1ded-256">Koleksiyonlar, dizinleri kullanmadan öğeleri eklemenize veya kaldırmanıza izin verdiklerinden, dizilerden kullanımı daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-256">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="a1ded-257">Kullanım kolaylığı nedeniyle, Koleksiyonlar genellikle formları ve denetimleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1ded-257">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a1ded-258">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="a1ded-258">Related topics</span></span>

<span data-ttu-id="a1ded-259">[İzlenecek yol: sınıfları tanımlama](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-259">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="a1ded-260">Sınıfının nasıl oluşturulacağı hakkında adım adım bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-260">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="a1ded-261">[Aşırı yüklenmiş Özellikler ve Yöntemler](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-261">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="a1ded-262">Aşırı Yüklenmiş Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a1ded-262">Overloaded Properties and Methods</span></span>

<span data-ttu-id="a1ded-263">[Devralma Temelleri](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-263">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="a1ded-264">Devralma değiştiricilerini, yöntemleri ve özellikleri geçersiz kılmayı, MyClass ve MyBase 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="a1ded-264">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="a1ded-265">[Nesne ömrü: nesneleri oluşturma ve yok etme](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-265">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="a1ded-266">Sınıf örneklerinin oluşturulmasını ve elden atılanışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-266">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="a1ded-267">[Anonim türler](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-267">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="a1ded-268">Veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanıza izin veren anonim türlerin nasıl oluşturulduğunu ve kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-268">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="a1ded-269">[Nesne başlatıcıları: adlandırılmış ve anonim türler](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-269">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="a1ded-270">Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-270">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="a1ded-271">[Nasıl yapılır: anonim tür bildirimlerinde özellik adlarını ve türleri Çıkarçıkar](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="a1ded-271">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="a1ded-272">Anonim tür bildirimlerinde özellik adlarının ve türlerin nasıl çıkarılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-272">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="a1ded-273">Başarılı ve başarısız çıkarım örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1ded-273">Provides examples of successful and unsuccessful inference.</span></span>
