---
title: Nesneler ve sınıflar Visual Basic'te
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 19aa20097e35a780f923a84e3e5809eb2b8bb3e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="28430-102">Nesneler ve sınıflar Visual Basic'te</span><span class="sxs-lookup"><span data-stu-id="28430-102">Objects and classes in Visual Basic</span></span>
<span data-ttu-id="28430-103">Bir *nesne* kod ve bir birim olarak kabul veri birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="28430-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="28430-104">Bir nesne bir denetim veya formun gibi bir uygulama bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="28430-105">Tüm uygulama aynı zamanda bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-105">An entire application can also be an object.</span></span>

<span data-ttu-id="28430-106">Visual Basic'te bir uygulama oluşturduğunuzda, sürekli nesneleri ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="28430-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="28430-107">Visual Basic tarafından sağlanan gibi denetimleri, formlar ve veri erişim nesneleri nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="28430-108">Visual Basic uygulamanızdaki diğer uygulamalardan nesne de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="28430-109">Hatta kendi nesneleri oluşturmak ve ek özellikleri ve yöntemleri kendileri için tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="28430-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="28430-110">Nesneleri hareket gibi prefabricated programlar için yapı taşları —, paylaştırılabilen bir kod kez yazma ve onu tekrar tekrar tekrar olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="28430-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>  
  
<span data-ttu-id="28430-111">Bu konuda nesneleri ayrıntılı ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="28430-111">This topic discusses objects in detail.</span></span>  

## <a name="objects-and-classes"></a><span data-ttu-id="28430-112">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="28430-112">Objects and classes</span></span>
<span data-ttu-id="28430-113">Visual Basic'te her nesne tarafından tanımlanan bir *sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="28430-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="28430-114">Bir sınıf değişkenleri, özellikleri, yordamlar ve olayları bir nesnenin açıklar.</span><span class="sxs-lookup"><span data-stu-id="28430-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="28430-115">Nesneleri sınıfların örnekleri olan; bir sınıf tanımladıktan sonra gereksinim duyduğunuz kadar çok nesneleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="28430-116">Bir nesne ve kendi sınıfı arasındaki ilişkiyi anlamak için tanımlama bilgisi cutters ve tanımlama bilgileri düşünün.</span><span class="sxs-lookup"><span data-stu-id="28430-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="28430-117">Tanımlama Bilgisi kesici sınıftır.</span><span class="sxs-lookup"><span data-stu-id="28430-117">The cookie cutter is the class.</span></span> <span data-ttu-id="28430-118">Örneğin boyutu ve şekli her tanımlama bilgisi özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28430-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="28430-119">Sınıf nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28430-119">The class is used to create objects.</span></span> <span data-ttu-id="28430-120">Tanımlama bilgilerini nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="28430-120">The objects are the cookies.</span></span>

<span data-ttu-id="28430-121">Üyeleri erişebilmeniz için önce bir nesne oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28430-121">You must create an object before you can access its members.</span></span>  

#### <a name="to-create-an-object-from-a-class"></a><span data-ttu-id="28430-122">Bir nesne öğesinden bir sınıf oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28430-122">To create an object from a class</span></span>

1. <span data-ttu-id="28430-123">Hangi sınıfından bir nesne oluşturmak istediğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="28430-123">Determine from which class you want to create an object.</span></span>  

2. <span data-ttu-id="28430-124">Yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) bir sınıf örneği atamak bir değişken oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="28430-124">Write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="28430-125">Değişkeni istenen sınıfı türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28430-125">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As customer
   ```

3. <span data-ttu-id="28430-126">Ekleme [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) sınıfının yeni bir örneğini değişkenine başlatmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="28430-126">Add the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New customer
   ```

4. <span data-ttu-id="28430-127">Bu gibi durumlarda, sınıf üyeleri şimdi nesne değişkeni erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-127">You can now access the members of the class through the object variable.</span></span>  

   ```vb
   nextCustomer.accountNumber = lastAccountNumber + 1  
   ```

> [!NOTE]
>  <span data-ttu-id="28430-128">Mümkün olduğunda, değişkenin kendisine atamak istiyorsanız sınıf türü olmasını bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28430-128">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="28430-129">Bu adlı *erken bağlama*.</span><span class="sxs-lookup"><span data-stu-id="28430-129">This is called *early binding*.</span></span> <span data-ttu-id="28430-130">Derleme zamanında yazın sınıfı bilmiyorsanız, çağırabileceği *geç bağlama* olması için değişken bildirme tarafından [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="28430-130">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="28430-131">Ancak, geç bağlama yavaş performans yapabilir ve çalışma zamanı nesnenin üyelerine erişimi sınırlamak.</span><span class="sxs-lookup"><span data-stu-id="28430-131">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="28430-132">Daha fazla bilgi için bkz: [nesne değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="28430-132">For more information, see [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="28430-133">Birden çok örneği</span><span class="sxs-lookup"><span data-stu-id="28430-133">Multiple instances</span></span>
<span data-ttu-id="28430-134">Yeni bir sınıftan oluşturulan genellikle birbirinin nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="28430-134">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="28430-135">Bireysel nesne olarak mevcut sonra ancak bunların değişkenlerin ve özelliklerin bağımsız olarak diğer örnekleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28430-135">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="28430-136">Üç onay kutularını bir forma eklerseniz, örneğin, her onay kutusu örneği nesnesidir <xref:System.Windows.Forms.CheckBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="28430-136">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="28430-137">Tek tek <xref:System.Windows.Forms.CheckBox> nesneleri özellikleri ve yetenekleri (özellikleri, değişkenleri, yordamlar ve olaylar) sınıf tarafından tanımlanan ortak bir dizi paylaşır.</span><span class="sxs-lookup"><span data-stu-id="28430-137">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="28430-138">Ancak, her biri kendi adına sahip, ayrı olarak etkinleştirilebilir ve devre dışı bırakıldı ve form üzerinde farklı bir konumda yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28430-138">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="28430-139">Nesne üyeleri</span><span class="sxs-lookup"><span data-stu-id="28430-139">Object members</span></span>
<span data-ttu-id="28430-140">Bir nesne bir uygulamanın bir öğedir temsil eden bir *örneği* bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="28430-140">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="28430-141">Alanlar, özellikleri, yöntemleri ve olayları nesnelerin yapı taşlarıdır ve oluşturan kendi *üyeleri*.</span><span class="sxs-lookup"><span data-stu-id="28430-141">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="28430-142">Üye Erişimi</span><span class="sxs-lookup"><span data-stu-id="28430-142">Member Access</span></span>
<span data-ttu-id="28430-143">Sırayla nesne değişkeninin adını belirterek bir nesnenin bir üyeye erişme bir süre (`.`) ve üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="28430-143">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="28430-144">Aşağıdaki örnek kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.Label> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28430-144">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="28430-145">Üyeleri IntelliSense listesi</span><span class="sxs-lookup"><span data-stu-id="28430-145">IntelliSense listing of members</span></span>
<span data-ttu-id="28430-146">Bir süre yazdığınızda, örneğin kendi listesi üyeleri seçeneği çağırdığınızda, IntelliSense listeler bir sınıf üyeleri (`.`) olarak bir üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="28430-146">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="28430-147">Ardından nokta bu sınıfının bir örneği bildirilen bir değişken adını yazarsanız, IntelliSense tüm örnek üyelerin ve paylaşılan üyeler hiçbiri listeler.</span><span class="sxs-lookup"><span data-stu-id="28430-147">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="28430-148">Sınıf adı şu süre yazarsanız, IntelliSense paylaşılan tüm üyeleri ve hiçbir örnek üyesinin listeler.</span><span class="sxs-lookup"><span data-stu-id="28430-148">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="28430-149">Daha fazla bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="28430-149">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="28430-150">Alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="28430-150">Fields and properties</span></span>
<span data-ttu-id="28430-151">*Alanları* ve *özellikleri* bir nesnesinde depolanan bilgiler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="28430-151">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="28430-152">Alabilir ve değerlerine atama deyimleri ile almak ve bir yordamda yerel değişkenleri ayarlamak aynı şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28430-152">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="28430-153">Aşağıdaki örnek alır <xref:System.Windows.Forms.Control.Width%2A> özelliği ve kümelerini <xref:System.Windows.Forms.Control.ForeColor%2A> özelliği bir <xref:System.Windows.Forms.Label> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28430-153">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="28430-154">Bir alan da adlandırılır Not bir *üye değişkeni*.</span><span class="sxs-lookup"><span data-stu-id="28430-154">Note that a field is also called a *member variable*.</span></span>
  
<span data-ttu-id="28430-155">Özellik yordamları kullanın zaman:</span><span class="sxs-lookup"><span data-stu-id="28430-155">Use property procedures when:</span></span>

- <span data-ttu-id="28430-156">Ne zaman ve nasıl bir değer alınan ya da denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28430-156">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="28430-157">Doğrulanması gereken değerleri iyi tanımlanmış bir dizi özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="28430-157">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="28430-158">Ayar değeri neden olan bazı algılanabilir değişiklik nesnenin durumda gibi bir `IsVisible` özelliği.</span><span class="sxs-lookup"><span data-stu-id="28430-158">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="28430-159">Özellik ayarı değişiklikleri diğer iç değişkenler veya diğer özelliklerin değerlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="28430-159">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="28430-160">Özelliği ayarlamak veya alınan önce adımlar gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="28430-160">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="28430-161">Alanları kullanın:</span><span class="sxs-lookup"><span data-stu-id="28430-161">Use fields when:</span></span>  

- <span data-ttu-id="28430-162">Kendi kendine doğrulama türü değerdir.</span><span class="sxs-lookup"><span data-stu-id="28430-162">The value is of a self-validating type.</span></span> <span data-ttu-id="28430-163">Örneğin, bir hata veya otomatik veri dönüştürme dışında bir değere saptanmışsa `True` veya `False` atanmış bir `Boolean` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="28430-163">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="28430-164">Veri türü tarafından desteklenen aralıkta herhangi bir değer geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="28430-164">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="28430-165">Bu tür birçok özelliği true ise `Single` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="28430-165">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="28430-166">Özelliği bir `String` veri türü ve boyutunu veya dize değeri hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="28430-166">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="28430-167">Daha fazla bilgi için bkz: [özellik yordamları](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="28430-167">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

### <a name="methods"></a><span data-ttu-id="28430-168">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28430-168">Methods</span></span>
<span data-ttu-id="28430-169">A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="28430-169">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="28430-170">Örneğin, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> bir yöntemi <xref:System.Windows.Forms.ComboBox> açılan kutuya yeni bir giriş eklemeden nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28430-170">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="28430-171">Aşağıdaki örnekte gösterilmiştir <xref:System.Windows.Forms.Timer.Start%2A> yöntemi bir <xref:System.Windows.Forms.Timer> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28430-171">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="28430-172">Bir yöntem yalnızca olduğuna dikkat edin bir *yordam* bir nesne tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="28430-172">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="28430-173">Daha fazla bilgi için bkz: [yordamları](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="28430-173">For more information, see [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="28430-174">Olaylar</span><span class="sxs-lookup"><span data-stu-id="28430-174">Events</span></span>
<span data-ttu-id="28430-175">Olaya yanıt vermesi için kod yazabilirsiniz ve fareyi tıklatarak veya bir tuşa basılması gibi bir nesne tarafından tanınan bir eylemdir.</span><span class="sxs-lookup"><span data-stu-id="28430-175">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="28430-176">Olayları bir kullanıcı eylemi veya program kodunun sonucu olarak ortaya çıkabilir veya sistem tarafından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-176">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="28430-177">Bir olay sinyalleri kod söyledi *yükseltmek* olay ve buna yanıt söyledi kodu *işlemek* onu.</span><span class="sxs-lookup"><span data-stu-id="28430-177">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="28430-178">Nesneleri tarafından oluşturulur ve diğer nesneleri tarafından işlenen için kendi özel olaylar da geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-178">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="28430-179">Daha fazla bilgi için bkz: [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="28430-179">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="28430-180">Örnek üyelerin ve paylaşılan üyeler</span><span class="sxs-lookup"><span data-stu-id="28430-180">Instance members and shared members</span></span>
<span data-ttu-id="28430-181">Bir sınıftan bir nesneyi oluşturduğunuzda, bu sınıfın örneğini sonucudur.</span><span class="sxs-lookup"><span data-stu-id="28430-181">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="28430-182">İle bildirilmemiş üyeleri [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) bir anahtar sözcüktür *örnek üyeleri*, ait oldukları kesinlikle için belirli Bu örneği.</span><span class="sxs-lookup"><span data-stu-id="28430-182">Members that are not declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="28430-183">Örnek üyesine bir örneği aynı sınıfın başka bir örneği aynı üye bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="28430-183">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="28430-184">Bir örnek üye değişkeni Örneğin, farklı durumlarda farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-184">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="28430-185">Üyeleri olarak bildirilen ile `Shared` bir anahtar sözcüktür *üyeleri Paylaşılan*, belirli bir örneği değil de, bir bütün olarak sınıfına ait.</span><span class="sxs-lookup"><span data-stu-id="28430-185">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="28430-186">Paylaşılan bir üyeye kaç sınıfın örnekleri, kendi olsun, oluşturduktan sonra ya da hiçbir örnekleri oluşturmak olsa bile bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28430-186">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="28430-187">Paylaşılan üye değişkeni, örneğin, sınıf erişebilen tüm kod için kullanılabilir olan tek bir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="28430-187">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-nonshared-members"></a><span data-ttu-id="28430-188">Paylaşılmayan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="28430-188">Accessing nonshared members</span></span>  

###### <a name="to-access-a-nonshared-member-of-an-object"></a><span data-ttu-id="28430-189">Paylaşılmayan bir nesne üyesi erişmek için</span><span class="sxs-lookup"><span data-stu-id="28430-189">To access a nonshared member of an object</span></span>

1. <span data-ttu-id="28430-190">Nesne kendi sınıfından oluşturulur ve bir nesne değişkenine atanan emin olun.</span><span class="sxs-lookup"><span data-stu-id="28430-190">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form  
   ```  

2. <span data-ttu-id="28430-191">Nesne değişken adında üye erişen deyiminde izleyin *üye erişimi işleci* (`.`) ve sonra üye adı.</span><span class="sxs-lookup"><span data-stu-id="28430-191">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="28430-192">Paylaşılan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="28430-192">Accessing shared members</span></span>

###### <a name="to-access-a-shared-member-of-an-object"></a><span data-ttu-id="28430-193">Paylaşılan bir nesne üyesi erişmek için</span><span class="sxs-lookup"><span data-stu-id="28430-193">To access a shared member of an object</span></span>

- <span data-ttu-id="28430-194">Sınıf adıyla izleyin *üye erişimi işleci* (`.`) ve sonra üye adı.</span><span class="sxs-lookup"><span data-stu-id="28430-194">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="28430-195">Her zaman erişim bir `Shared` nesnesinin sınıf adı aracılığıyla doğrudan üyesi.</span><span class="sxs-lookup"><span data-stu-id="28430-195">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   MsgBox("This computer is called " & Environment.MachineName)  
   ```

- <span data-ttu-id="28430-196">Sınıfından bir nesne zaten oluşturduysanız, alternatif olarak erişebileceğiniz bir `Shared` nesne değişkeni aracılığıyla üye.</span><span class="sxs-lookup"><span data-stu-id="28430-196">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="28430-197">Sınıfları ve modülleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="28430-197">Differences between classes and modules</span></span>
<span data-ttu-id="28430-198">Sınıfları ve modülleri arasındaki temel fark, standart modüller işleyemez sınıfları nesneler olarak oluşturulabilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="28430-198">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="28430-199">Programınızı bir bölümünü standart modül ortak bir değişkende değiştiğinde standart modülünün verilerin yalnızca bir kopya olduğundan daha sonra bu değişkeni okur varsa herhangi bir programın parçası aynı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="28430-199">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="28430-200">Buna karşılık, nesne verileri başlatılan her nesne için ayrı olarak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28430-200">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="28430-201">Standart modüller, sınıflar arabirimleri uygulayabilir başka bir farktır.</span><span class="sxs-lookup"><span data-stu-id="28430-201">Another difference is that unlike standard modules, classes can implement interfaces.</span></span>

> [!NOTE]
> <span data-ttu-id="28430-202">Zaman `Shared` değiştiricisi sınıf üyesi uygulandığında, sınıfın kendisi yerine belirli bir sınıfın örneği ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="28430-202">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="28430-203">Üye doğrudan sınıf adı kullanılarak erişilir, aynı şekilde modülü üyeleri erişilir.</span><span class="sxs-lookup"><span data-stu-id="28430-203">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="28430-204">Sınıfları ve modüller de üyeleri için farklı kapsamlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="28430-204">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="28430-205">Üyeleri bir sınıf içinde tanımlanan belirli bir sınıfın örneği içinde kapsamlı ve yalnızca nesne yaşam süresi için mevcut.</span><span class="sxs-lookup"><span data-stu-id="28430-205">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="28430-206">Sınıf dışındaki sınıfı üyelerinden erişmek için tam olarak nitelenmiş adlar biçiminde kullanmalısınız *nesne*. *Üye*.</span><span class="sxs-lookup"><span data-stu-id="28430-206">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="28430-207">Öte yandan, bir modül içinde bildirilen üyeleri varsayılan olarak genel olarak erişilebilir ve modülü erişmek için herhangi bir kod erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="28430-207">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="28430-208">Standart modülde değişkenleri etkili bir şekilde genel değişkenler herhangi bir yere projenizde görünür olduğundan ve program ömrü için var olan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28430-208">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="28430-209">Sınıfları ve nesneleri yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="28430-209">Reusing classes and objects</span></span>  
<span data-ttu-id="28430-210">Nesneleri, değişken ve yordamların bir kez bildirme ve bunları gerektiğinde yeniden olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="28430-210">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="28430-211">Örneğin, yazım denetleyicisi uygulama eklemek istiyorsanız, tüm değişkenleri tanımlayın ve yazım denetimi işlevselliği sağlamak için işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="28430-211">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="28430-212">Yazım bir sınıf olarak oluşturursanız, daha sonra onu diğer uygulamalarda derlenmiş derlemesine başvuru ekleyerek tekrar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28430-212">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="28430-213">Daha iyi henüz başka birisi zaten geliştirmiştir yazım sınıfını kullanarak kendiniz bazı iş kaydetmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-213">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="28430-214">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Kullanılabilir bileşenleri birçok örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="28430-214">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provides many examples of components that are available for use.</span></span> <span data-ttu-id="28430-215">Aşağıdaki örnek kullanır <xref:System.TimeZone> sınıfını <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="28430-215">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="28430-216"><xref:System.TimeZone> Geçerli bilgisayar sistemi saat dilimi hakkında bilgi almaya izin üyeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="28430-216"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

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

<span data-ttu-id="28430-217">Önceki örnekte, ilk [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) türünde bir nesne değişkeni bildirir <xref:System.TimeZone> ve atar bir <xref:System.TimeZone> tarafından döndürülen nesne <xref:System.TimeZone.CurrentTimeZone%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="28430-217">In the preceding example, the first [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="28430-218">Nesneleri arasındaki ilişki</span><span class="sxs-lookup"><span data-stu-id="28430-218">Relationships among objects</span></span>  
<span data-ttu-id="28430-219">Nesneler birbirine çeşitli yollarla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28430-219">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="28430-220">İlişkinin asıl türleridir *hiyerarşik* ve *kapsama*.</span><span class="sxs-lookup"><span data-stu-id="28430-220">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="28430-221">Hiyerarşik bir ilişki</span><span class="sxs-lookup"><span data-stu-id="28430-221">Hierarchical relationship</span></span>
<span data-ttu-id="28430-222">Daha fazla temel sınıflarından türetilmiş sınıfları, bunlar sahip söylenir bir *hiyerarşik bir ilişki*.</span><span class="sxs-lookup"><span data-stu-id="28430-222">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="28430-223">Sınıf hiyerarşileri daha genel bir sınıfın alt öğeleri açıklayan yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="28430-223">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="28430-224">Aşağıdaki örnekte, bir özel tür tanımlamak istediğiniz varsayalım <xref:System.Windows.Forms.Button> normal gibi davranır <xref:System.Windows.Forms.Button> ancak aynı zamanda ön ve arka plan renkleri ters çevirir bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="28430-224">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

##### <a name="to-define-a-class-is-derived-from-an-already-existing-class"></a><span data-ttu-id="28430-225">Bir sınıf tanımlama zaten varolan bir sınıftan türetilen</span><span class="sxs-lookup"><span data-stu-id="28430-225">To define a class is derived from an already existing class</span></span>

1. <span data-ttu-id="28430-226">Kullanım bir [Class deyimi](../../../../visual-basic/language-reference/statements/class-statement.md) , nesneyi oluşturmak için gereksinim duyduğunuz bir sınıf tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="28430-226">Use a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class reversibleButton
   ```

   <span data-ttu-id="28430-227">Mutlaka bir `End Class` deyimi sınıfınızda kodu son satırının izler.</span><span class="sxs-lookup"><span data-stu-id="28430-227">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="28430-228">Varsayılan olarak, tümleşik geliştirme ortamı (IDE) otomatik olarak oluşturan bir `End Class` girdiğinizde bir `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="28430-228">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="28430-229">İzleyin `Class` deyimiyle hemen bir [Inherits deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="28430-229">Follow the `Class` statement immediately with an [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="28430-230">Yeni sınıfınıza türetilen sınıf belirtin.</span><span class="sxs-lookup"><span data-stu-id="28430-230">Specify the class from which your new class derives.</span></span>  
  
   ```vb
   Inherits System.Windows.Forms.Button
   ```

  <span data-ttu-id="28430-231">Yeni sınıfınıza temel sınıf tarafından tanımlanan tüm üyeleri devralır.</span><span class="sxs-lookup"><span data-stu-id="28430-231">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="28430-232">Kodu ek üyeler için türetilmiş sınıf çıkarır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28430-232">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="28430-233">Örneğin, eklemiş olabileceğiniz bir `reverseColors` yöntemi ve türetilmiş sınıf görünebilir gibi:</span><span class="sxs-lookup"><span data-stu-id="28430-233">For example, you might add a `reverseColors` method, and your derived class might look as follows:</span></span>

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

   <span data-ttu-id="28430-234">Bir nesneden oluşturursanız `reversibleButton` sınıfı, tüm üyeleri erişebilir <xref:System.Windows.Forms.Button> sınıfı, yanı sıra `reverseColors` yöntemi ve tanımladığınız üzerindeki diğer yeni üyeler `reversibleButton`.</span><span class="sxs-lookup"><span data-stu-id="28430-234">If you create an object from the `reversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `reverseColors` method and any other new members you define on `reversibleButton`.</span></span>

<span data-ttu-id="28430-235">Türetilen sınıflar, ilerledikçe karmaşıklık sınıf hiyerarşisinde eklemenize olanak sağlayan temel sınıfı üyeleri devralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28430-235">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="28430-236">Daha fazla bilgi için bkz: [devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="28430-236">For more information, see [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

#### <a name="compiling-the-code"></a><span data-ttu-id="28430-237">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="28430-237">Compiling the code</span></span>
<span data-ttu-id="28430-238">Derleyici, yeni bir sınıf türetin istediğiniz sınıfı erişebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="28430-238">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="28430-239">Bu tam adı, önceki örnekte olduğu gibi niteleme veya kendi ad alanında tanımlayan anlamına gelebilir bir [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="28430-239">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="28430-240">Sınıf farklı projesiyse, bu proje bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="28430-240">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="28430-241">Daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="28430-241">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="28430-242">Kapsama ilişkisi</span><span class="sxs-lookup"><span data-stu-id="28430-242">Containment relationship</span></span>
<span data-ttu-id="28430-243">Nesneleri ilgili başka bir yolu bir *kapsama ilişkisi*.</span><span class="sxs-lookup"><span data-stu-id="28430-243">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="28430-244">Kapsayıcı nesneleri diğer nesnelerin mantıksal olarak kapsüller.</span><span class="sxs-lookup"><span data-stu-id="28430-244">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="28430-245">Örneğin, <xref:System.OperatingSystem> nesnesini mantıksal olarak içeren bir <xref:System.Version> aracılığıyla döndürür nesne, kendi <xref:System.OperatingSystem.Version%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="28430-245">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="28430-246">Kapsayıcı nesne fiziksel olarak başka bir nesneyi içermiyor unutmayın.</span><span class="sxs-lookup"><span data-stu-id="28430-246">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="28430-247">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="28430-247">Collections</span></span>
<span data-ttu-id="28430-248">Belirli bir nesne kapsama türü ile temsil edilir *koleksiyonları*.</span><span class="sxs-lookup"><span data-stu-id="28430-248">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="28430-249">Koleksiyonları sıralanabilecek nesneleri gruplarıdır.</span><span class="sxs-lookup"><span data-stu-id="28430-249">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="28430-250">Visual Basic destekler içindeki belirli bir sözdizimi [For Each... Sonraki deyim](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) koleksiyonu öğeler arasında yinelemek izin verir.</span><span class="sxs-lookup"><span data-stu-id="28430-250">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="28430-251">Ayrıca, koleksiyonlar çoğunlukla kullanmanıza olanak sağlayan bir <xref:Microsoft.VisualBasic.Collection.Item%2A> kendi dizini veya benzersiz bir dize ile ilişkilendirerek öğeleri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="28430-251">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="28430-252">Koleksiyonlar eklemek veya dizinleri kullanmadan öğeleri kaldırmak izin verdiğinden diziler kullanmak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="28430-252">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="28430-253">Bunların kullanım kolaylığı nedeniyle, koleksiyonlar çoğunlukla formlar ve denetimler depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28430-253">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="28430-254">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="28430-254">Related topics</span></span>  
 [<span data-ttu-id="28430-255">İzlenecek Yol: Sınıfları Tanımlama</span><span class="sxs-lookup"><span data-stu-id="28430-255">Walkthrough: Defining Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 <span data-ttu-id="28430-256">Bir sınıfın nasıl oluşturulacağı hakkında adım adım bir açıklaması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="28430-256">Provides a step-by-step description of how to create a class.</span></span>  

 [<span data-ttu-id="28430-257">Aşırı Yüklenmiş Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28430-257">Overloaded Properties and Methods</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 <span data-ttu-id="28430-258">Aşırı Yüklenmiş Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28430-258">Overloaded Properties and Methods</span></span>  

 [<span data-ttu-id="28430-259">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="28430-259">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="28430-260">Devralma değiştiriciler, yöntemleri ve özellikleri, MyClass ve MyBase geçersiz kılma kapsar.</span><span class="sxs-lookup"><span data-stu-id="28430-260">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>  

 [<span data-ttu-id="28430-261">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="28430-261">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 <span data-ttu-id="28430-262">Oluşturma ve sınıf örneklerini atma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="28430-262">Discusses creating and disposing of class instances.</span></span>  

 [<span data-ttu-id="28430-263">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="28430-263">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 <span data-ttu-id="28430-264">Oluşturma ve veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmanıza izin anonim türler kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="28430-264">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>  

 [<span data-ttu-id="28430-265">Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="28430-265">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 <span data-ttu-id="28430-266">Tek bir ifade kullanarak adlandırılmış ve anonim türler örneklerini oluşturmak için kullanılan nesne başlatıcıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="28430-266">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>  

 [<span data-ttu-id="28430-267">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="28430-267">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 <span data-ttu-id="28430-268">Özellik adlarını ve türlerini anonim türde bildirimlerden çıkarma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28430-268">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="28430-269">Başarılı ve başarısız çıkarım örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="28430-269">Provides examples of successful and unsuccessful inference.</span></span>
