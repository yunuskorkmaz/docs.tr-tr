---
title: Nesneler ve sınıflar Visual Basic'te
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: ec5825dacaf67ee2544302f4f95a1b341ecf1bf7
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807865"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="b6ceb-102">Nesneler ve sınıflar Visual Basic'te</span><span class="sxs-lookup"><span data-stu-id="b6ceb-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="b6ceb-103">Bir *nesne* kod ve bir birim olarak davranılıp veri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="b6ceb-104">Bir nesne gibi bir denetim veya form uygulamanın bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="b6ceb-105">Tüm uygulama ayrıca bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-105">An entire application can also be an object.</span></span>

<span data-ttu-id="b6ceb-106">Visual Basic'te bir uygulama oluşturduğunuzda, sürekli nesnelerle çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="b6ceb-107">Visual Basic tarafından sağlanan gibi denetimleri, formlar ve veri erişim nesneleri nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="b6ceb-108">Visual Basic uygulamanızdaki diğer uygulamalardan nesneler de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="b6ceb-109">Hatta, kendi nesnelerinizi oluşturma ve ek özellikleri ve yöntemleri için bunları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="b6ceb-110">Nesneler davranır gibi prefabricated programlar için yapı taşları — bunlar, bir parça kodu bir kere yazıp, onu tekrar tekrar tekrar olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="b6ceb-111">Bu konuda, nesneleri ayrıntılı ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="b6ceb-112">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="b6ceb-112">Objects and classes</span></span>

<span data-ttu-id="b6ceb-113">Visual Basic'te her nesne tarafından tanımlanan bir *sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="b6ceb-114">Bir sınıf, değişkenleri, özellikleri, yordamları ve olayları bir nesnenin açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="b6ceb-115">Sınıfların örneklerini nesnelerdir; bir sınıf tanımlandıktan ihtiyacınız kadar nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="b6ceb-116">Bir nesne ve onun sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgileri düşünün.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="b6ceb-117">Tanımlama Bilgisi kesici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-117">The cookie cutter is the class.</span></span> <span data-ttu-id="b6ceb-118">Bu özellikleri her tanımlama bilgisi boyutu ve şekli tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="b6ceb-119">Sınıf nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-119">The class is used to create objects.</span></span> <span data-ttu-id="b6ceb-120">Tanımlama bilgilerini nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-120">The objects are the cookies.</span></span>

<span data-ttu-id="b6ceb-121">Üyeleri erişebilmeniz için önce bir nesne oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-121">You must create an object before you can access its members.</span></span>

#### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="b6ceb-122">Nesne öğesinden bir sınıf oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b6ceb-122">To create an object from a class</span></span>

1. <span data-ttu-id="b6ceb-123">Hangi sınıfından bir nesne oluşturmak istediğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-123">Determine from which class you want to create an object.</span></span>

2. <span data-ttu-id="b6ceb-124">Yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) bir sınıf örneği atamak bir değişken oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="b6ceb-125">Değişkeni istenen sınıf türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="b6ceb-126">Ekleme [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) değişkene sınıfının yeni bir örneğini başlatmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="b6ceb-127">Nesne değişkeni sınıf üyeleri artık erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-127">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="b6ceb-128">Mümkün olduğunda, atamak istediğiniz sınıf türünün olmasını değişkeni bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="b6ceb-129">Bu adlandırılır *erken bağlama*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-129">This is called *early binding*.</span></span> <span data-ttu-id="b6ceb-130">Derleme zamanında tür sınıfı bilmiyorsanız, çağırabilirsiniz *geç bağlama* olmaya değişken bildirme tarafından [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="b6ceb-131">Ancak geç bağlama performans daha yavaş hale ve çalışma zamanı nesnenin üyelerine erişimi sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="b6ceb-132">Daha fazla bilgi için [nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="b6ceb-133">Birden çok örneği</span><span class="sxs-lookup"><span data-stu-id="b6ceb-133">Multiple instances</span></span>

<span data-ttu-id="b6ceb-134">Yeni bir sınıftan oluşturulan nesneler genellikle birbirinin.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="b6ceb-135">Bireysel nesne olarak oldukları sonra Bununla birlikte, kendi değişkenleri ve özellikleri diğer örneklerin bağımsız olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="b6ceb-136">Üç onay kutusunu forma eklerseniz, örneğin, onay kutusu her bir nesne örneğidir <xref:System.Windows.Forms.CheckBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="b6ceb-137">Tek tek <xref:System.Windows.Forms.CheckBox> nesneleri özellikleri ve sınıf tarafından tanımlanan özellikleri (özellikleri, değişkenleri, yordamları ve olayları) ortak bir kümesini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="b6ceb-138">Ancak, her kendi adına sahip, ayrı ayrı etkinleştirilebilir ve devre dışı bırakıldı ve form üzerinde farklı bir konumda yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="b6ceb-139">Nesne üyeleri</span><span class="sxs-lookup"><span data-stu-id="b6ceb-139">Object members</span></span>

<span data-ttu-id="b6ceb-140">Bir uygulamanın bir öğe bir nesnedir temsil eden bir *örneği* bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="b6ceb-141">Alanlar, özellikler, yöntemler ve olaylar yapı taşlarıdır nesnelerin ve oluşturan kendi *üyeleri*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="b6ceb-142">Üye Erişimi</span><span class="sxs-lookup"><span data-stu-id="b6ceb-142">Member Access</span></span>

<span data-ttu-id="b6ceb-143">Sırasıyla nesne değişkeni adını belirterek bir nesnenin bir üyesine erişmek bir süre (`.`) ve üyesinin adı.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="b6ceb-144">Aşağıdaki örnek kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.Label> nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="b6ceb-145">IntelliSense üye listesi</span><span class="sxs-lookup"><span data-stu-id="b6ceb-145">IntelliSense listing of members</span></span>

<span data-ttu-id="b6ceb-146">IntelliSense, bir nokta yazın, örneğin, üyeleri Listele seçeneğini çağırdığınızda, bir sınıfın üyeleri listeler (`.`) üye erişim işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="b6ceb-147">Bu sınıfın bir örneği bildirilen bir değişken adını ardından nokta yazarsanız, IntelliSense, tüm örnek üyeleri ve paylaşılan üyeler hiçbiri listeler.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="b6ceb-148">Sınıf adı nokta yazarsanız, IntelliSense, tüm paylaşılan üyeleri ve örnek üyeleri hiçbiri listeler.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="b6ceb-149">Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="b6ceb-150">Alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="b6ceb-150">Fields and properties</span></span>

<span data-ttu-id="b6ceb-151">*Alanları* ve *özellikleri* bir nesnede depolanan bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="b6ceb-152">Alabilir ve aynı şekilde almak ve bir yordamda yerel değişkenleri ayarlamak değerlerine atama deyimleri ile ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="b6ceb-153">Aşağıdaki örnek alır <xref:System.Windows.Forms.Control.Width%2A> özelliği ve kümelerini <xref:System.Windows.Forms.Control.ForeColor%2A> özelliği bir <xref:System.Windows.Forms.Label> nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="b6ceb-154">Bir alan da çağrıldığını unutmayın bir *üye değişkeni*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-154">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="b6ceb-155">Özellik yordamları kullanın. zaman:</span><span class="sxs-lookup"><span data-stu-id="b6ceb-155">Use property procedures when:</span></span>

- <span data-ttu-id="b6ceb-156">Ne zaman ve nasıl bir değer alındı veya ayarlandığında denetlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="b6ceb-157">Doğrulanması gereken, iyi tanımlanmış bir dizi özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="b6ceb-158">Ayar değeri neden olan bazı bir algılanabilir değişiklik nesnenin durumda gibi bir `IsVisible` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="b6ceb-159">Özelliğini, diğer iç değişkenler veya diğer özelliklerin değerlerine değişiklikler neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="b6ceb-160">Özelliği ayarlamak veya alınan adımlar gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="b6ceb-161">Alanları kullanın:</span><span class="sxs-lookup"><span data-stu-id="b6ceb-161">Use fields when:</span></span>

- <span data-ttu-id="b6ceb-162">Kendi kendine doğrulama türü değerdir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-162">The value is of a self-validating type.</span></span> <span data-ttu-id="b6ceb-163">Örneğin, bir hata veya otomatik veri dönüştürme dışında bir değere oluşur `True` veya `False` atanan bir `Boolean` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="b6ceb-164">Veri türü tarafından desteklenen aralıkta herhangi bir değer geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="b6ceb-165">Bu tür birçok özelliği true `Single` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="b6ceb-166">Özelliği bir `String` veri türünü ve boyutunu veya dize değeri hiçbir kısıtlaması yoktur.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="b6ceb-167">Daha fazla bilgi için [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="b6ceb-168">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b6ceb-168">Methods</span></span>

<span data-ttu-id="b6ceb-169">A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="b6ceb-170">Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> bir yöntemidir <xref:System.Windows.Forms.ComboBox> nesnesini bir birleşik giriş kutusuna yeni bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="b6ceb-171">Aşağıdaki örnek, gösterir <xref:System.Windows.Forms.Timer.Start%2A> yöntemi bir <xref:System.Windows.Forms.Timer> nesne.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="b6ceb-172">Yalnızca bir yöntem olduğunu unutmayın bir *yordamı* nesne tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="b6ceb-173">Daha fazla bilgi için [yordamları](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="b6ceb-174">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b6ceb-174">Events</span></span>

<span data-ttu-id="b6ceb-175">Bir olay yanıt vermesi için kod yazabilirsiniz ve fareyle tıklamak veya bir tuşuna basmak gibi bir nesne tarafından tanınan bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="b6ceb-176">Olayları bir kullanıcı eylemi veya program kodu sonucunda oluşabilir veya sistem tarafından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="b6ceb-177">Bir olay sinyalini verir kod söyledi *yükseltmek* olay ve buna yanıt diyor ki kod *işlemek* bu.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="b6ceb-178">Nesnelerinizi tarafından oluşturulur ve diğer nesneleri tarafından işlenen özel kendi olaylarınızı da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="b6ceb-179">Daha fazla bilgi için [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="b6ceb-180">Örnek üyeleri ve paylaşılan üyeler</span><span class="sxs-lookup"><span data-stu-id="b6ceb-180">Instance members and shared members</span></span>

<span data-ttu-id="b6ceb-181">Öğesinden bir sınıf bir nesne oluşturduğunuzda, bu sınıfın bir örneğini sonucudur.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="b6ceb-182">İle bildirilmiş üyeleri [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) anahtar sözcüğünü *örnek üyeleri*, ait oldukları kesinlikle, belirli bir örneğine.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="b6ceb-183">Bir örnek üyesi bir örneği, başka bir örneğinin aynı sınıfta aynı üye bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="b6ceb-184">Bir örnek üye değişkeni, örneğin, farklı durumlarda farklı değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="b6ceb-185">Bildirilen üyeleri ile `Shared` anahtar sözcüğünü *üyeleri Paylaşılan*, bir bütün olarak sınıfı ve herhangi belirli bir örneğine ait.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="b6ceb-186">Paylaşılan üye sınıfının kaç tane ne olursa olsun, oluşturduktan sonra ya da hiçbir örneği oluşturmak olsa bile var.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="b6ceb-187">Paylaşılan üye değişkeni, örneğin, sınıf erişebilen tüm kod için kullanılabilir olan yalnızca bir değer var.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="b6ceb-188">Paylaşılmayan üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="b6ceb-188">Accessing nonshared members</span></span>

###### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="b6ceb-189">Bir nesnenin paylaşılmayan bir üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="b6ceb-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="b6ceb-190">Nesnenin kendi sınıfından oluşturulur ve bir nesne değişkenine atanan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="b6ceb-191">Nesnenin değişken adıyla üye erişen deyiminde izleyin *üye erişim işleci* (`.`) ve ardından üye adı.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="b6ceb-192">Paylaşılan üyelerine erişme</span><span class="sxs-lookup"><span data-stu-id="b6ceb-192">Accessing shared members</span></span>

###### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="b6ceb-193">Bir nesnenin paylaşılan bir üyesine erişmek için</span><span class="sxs-lookup"><span data-stu-id="b6ceb-193">To access a shared member of an object</span></span>

- <span data-ttu-id="b6ceb-194">Sınıf adını izleyin *üye erişim işleci* (`.`) ve ardından üye adı.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="b6ceb-195">Her zaman erişmeli bir `Shared` nesnenin sınıf adı aracılığıyla doğrudan üyesi.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="b6ceb-196">Sınıfından bir nesne zaten oluşturduysanız, alternatif olarak erişebileceğiniz bir `Shared` üye nesne değişkeni aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="b6ceb-197">Sınıflar ve modüller arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="b6ceb-197">Differences between classes and modules</span></span>

<span data-ttu-id="b6ceb-198">Sınıflar ve modüller arasındaki temel fark, standart modüller işleyemez sınıfları nesneler olarak oluşturulabilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="b6ceb-199">Standart Modül içindeki genel bir değişken, programın bir parçası değiştiğinde verileri standart bir modülün, yalnızca bir kopyası olduğundan daha sonra bu değişkene okur, herhangi bir programın parçası aynı değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="b6ceb-200">Buna karşılık, nesne verileri, her örneklenen bir nesne için ayrı olarak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="b6ceb-201">Standart modüller, sınıflar arabirimleri uygulayabilir başka bir farktır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="b6ceb-202">Zaman `Shared` değiştiricisi bir sınıf üyesine uygulandığında, sınıfın kendisi yerine belirli bir sınıfın örneğini ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="b6ceb-203">Üye sınıfı adı kullanarak doğrudan erişilir, aynı şekilde modülü üyeleri erişilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="b6ceb-204">Sınıflar ve modüller de üyeleri için farklı kapsamlar kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="b6ceb-205">Bir sınıf içinde tanımlanmış üyeler içinde belirli bir sınıfın örneğini kapsamlı ve nesne ömrü boyunca yalnızca mevcut.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="b6ceb-206">Sınıf üyeleri sınıf dışındaki erişmek için tam olarak nitelenmiş adlar biçiminde kullanmalısınız *nesne*. *Üye*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="b6ceb-207">İçinde bir modül olarak bildirilen üyeler Öte yandan, varsayılan olarak genel olarak erişilebilir olduğundan emin olun ve modül erişebilen herhangi kod tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="b6ceb-208">Standart Modül içindeki değişkenler etkili bir şekilde genel değişkenler, projenizdeki herhangi bir yerde görünür olduklarını ve bunlar program süresince mevcut olduğu bu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="b6ceb-209">Sınıfları ve nesneleri yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="b6ceb-209">Reusing classes and objects</span></span>

<span data-ttu-id="b6ceb-210">Nesneler, değişkenler ve yordamlar bildirmek ve daha sonra gerektiğinde bunları yeniden olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="b6ceb-211">Örneğin, yazım denetleyicisi uygulama eklemek istiyorsanız, tüm değişkenleri tanımlayın ve yazım denetimi işlevselliği sağlamak için işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="b6ceb-212">Yazım sınıf olarak oluşturursanız, ardından onu diğer uygulamalarda derlenmiş derlemesine bir başvuru ekleyerek tekrar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="b6ceb-213">Üstelik başka birisi zaten geliştirmiştir bir yazım denetleyicisi sınıfını kullanarak bazı iş kendiniz kaydetmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="b6ceb-214">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Pek çok kullanımı için uygun olan bileşenleri örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-214">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provides many examples of components that are available for use.</span></span> <span data-ttu-id="b6ceb-215">Aşağıdaki örnekte <xref:System.TimeZone> sınıfını <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="b6ceb-216"><xref:System.TimeZone> Geçerli bilgisayar sisteminin saat dilimi hakkında bilgi almanıza olanak tanıyan üyeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

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

<span data-ttu-id="b6ceb-217">Yukarıdaki örnekte, ilk [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) türünde bir nesne değişkeni bildirir <xref:System.TimeZone> ve buna atayan bir <xref:System.TimeZone> tarafından döndürülen nesne <xref:System.TimeZone.CurrentTimeZone%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="b6ceb-218">Nesneleri arasındaki ilişki</span><span class="sxs-lookup"><span data-stu-id="b6ceb-218">Relationships among objects</span></span>

<span data-ttu-id="b6ceb-219">Çeşitli yollarla nesneleri birbirleriyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="b6ceb-220">İlişki asıl türde *hiyerarşik* ve *kapsama*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="b6ceb-221">Hiyerarşi ilişkisi</span><span class="sxs-lookup"><span data-stu-id="b6ceb-221">Hierarchical relationship</span></span>

<span data-ttu-id="b6ceb-222">Daha fazla temel sınıftan türetilmiş sınıflar, bunlar olduğu söylenir ve bir *hiyerarşik ilişkiyi*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="b6ceb-223">Sınıf Hiyerarşiler daha genel bir sınıf türünün bir alt öğeleri açıklayan yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="b6ceb-224">Aşağıdaki örnekte, özel bir tür tanımlamak istediğiniz varsayalım <xref:System.Windows.Forms.Button> normal gibi davranır <xref:System.Windows.Forms.Button> ancak aynı zamanda ön ve arka plan renkleri tersine bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="b6ceb-225">Zaten varolan bir sınıftan türetildiği durumda olduğu bir sınıf tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b6ceb-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="b6ceb-226">Kullanım bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md) , nesneyi oluşturmak için ihtiyacınız olan bir sınıf tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="b6ceb-227">Mutlaka bir `End Class` deyimini sınıfınıza kodda son satırının izler.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="b6ceb-228">Varsayılan olarak, tümleşik geliştirme ortamı (IDE) otomatik olarak oluşturduğu bir `End Class` girdiğinizde bir `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="b6ceb-229">İzleyin `Class` deyimiyle hemen bir [devralan deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="b6ceb-230">Yeni sınıfınıza türetildiği sınıf belirtin.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-230">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="b6ceb-231">Yeni sınıfınıza taban sınıfı tarafından tanımlanan tüm üyelerini devralır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="b6ceb-232">Kod, türetilmiş sınıf üzerinden kullanıma sunan ek üyelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="b6ceb-233">Örneğin, eklemiş olabileceğiniz bir `reverseColors` yöntemi ve türetilmiş sınıfınızın görünebilir gibi:</span><span class="sxs-lookup"><span data-stu-id="b6ceb-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

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

   <span data-ttu-id="b6ceb-234">Bir nesneden oluşturursanız `reversibleButton` sınıfı, bunu tüm üyelerine erişebilir <xref:System.Windows.Forms.Button> sınıfı, hem de `reverseColors` yöntemi ve tanımladığınız üzerinde diğer herhangi bir yeni üye `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="b6ceb-235">Türetilen sınıfların üyeleri, siz ilerledikçe karmaşıklığı bir sınıf hiyerarşisi içinde eklemenize olanak sağlayan temel sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="b6ceb-236">Daha fazla bilgi için [devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

#### <a name="compiling-the-code"></a><span data-ttu-id="b6ceb-237">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="b6ceb-237">Compiling the code</span></span>

<span data-ttu-id="b6ceb-238">Derleyici, yeni bir sınıf türetmek istediğinize sınıfı erişebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="b6ceb-239">Bu tam adı, önceki örnekte olduğu gibi uygun veya kendi ad alanında tanımlayan gelebilir bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="b6ceb-240">Farklı bir projedeki sınıf ise bu projeye bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="b6ceb-241">Daha fazla bilgi için [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="b6ceb-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="b6ceb-242">Kapsama ilişkisi</span><span class="sxs-lookup"><span data-stu-id="b6ceb-242">Containment relationship</span></span>

<span data-ttu-id="b6ceb-243">Nesnenin ilgili başka bir yolu ise bir *kapsama ilişkisi*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="b6ceb-244">Kapsayıcı nesneleri, diğer nesnelerin mantıksal kapsüller.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="b6ceb-245">Örneğin, <xref:System.OperatingSystem> nesne mantıksal olarak içeren bir <xref:System.Version> aracılığıyla döndüren bir nesne kendi <xref:System.OperatingSystem.Version%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="b6ceb-246">Not kapsayıcı nesne fiziksel olarak herhangi bir nesne içermiyor.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="b6ceb-247">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="b6ceb-247">Collections</span></span>

<span data-ttu-id="b6ceb-248">Nesne kapsama belirli bir tür tarafından temsil edilen *koleksiyonları*.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="b6ceb-249">Numaralandırılabilir benzer nesne koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="b6ceb-250">Visual Basic, belirli bir söz dizimi destekler [her biri için... Sonraki deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) bir koleksiyonun öğeleri yineleme yapmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="b6ceb-251">Ayrıca, koleksiyonlar çoğunlukla kullanmanıza olanak sağlayan bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kendi dizini veya benzersiz bir dize ile ilişkilendirerek öğeleri almak için.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="b6ceb-252">Koleksiyonlar eklemek veya dizinleri kullanmadan öğeleri kaldırmak izin verdiğinden dizileri kullanmak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="b6ceb-253">Kendi kullanım kolaylığı nedeniyle, koleksiyonlar genellikle formlar ve denetimler depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b6ceb-254">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="b6ceb-254">Related topics</span></span>

<span data-ttu-id="b6ceb-255">[İzlenecek yol: Sınıfları tanımlama](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-255">[Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)\\</span></span>
<span data-ttu-id="b6ceb-256">Bir sınıf oluşturma adım adım bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-256">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="b6ceb-257">[Aşırı yüklenmiş özellikler ve yöntemler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-257">[Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)\\</span></span>
<span data-ttu-id="b6ceb-258">Aşırı Yüklenmiş Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b6ceb-258">Overloaded Properties and Methods</span></span>

<span data-ttu-id="b6ceb-259">[Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-259">[Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)\\</span></span>
<span data-ttu-id="b6ceb-260">Devralma değiştiriciler, yöntemleri ve özellikleri ve MyClass MyBase geçersiz kılma kapsar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="b6ceb-261">[Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-261">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)\\</span></span>
<span data-ttu-id="b6ceb-262">Oluşturma ve sınıf örneklerini disposing açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-262">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="b6ceb-263">[Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-263">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)\\</span></span>
<span data-ttu-id="b6ceb-264">Veri türü için bir sınıf tanımı yazmak zorunda kalmadan nesneleri oluşturmanızı sağlayan anonim türler oluşturup kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="b6ceb-265">[Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-265">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)\\</span></span>
<span data-ttu-id="b6ceb-266">Tek bir ifade kullanarak adlandırılmış ve anonim türlerin örneklerini oluşturmak için kullanılan nesne başlatıcıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="b6ceb-267">[Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\\</span><span class="sxs-lookup"><span data-stu-id="b6ceb-267">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)\\</span></span>
<span data-ttu-id="b6ceb-268">Özellik adları ve türleri anonim türde bildirimlerden çıkarma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="b6ceb-269">Başarılı ve başarısız çıkarımı örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b6ceb-269">Provides examples of successful and unsuccessful inference.</span></span>
