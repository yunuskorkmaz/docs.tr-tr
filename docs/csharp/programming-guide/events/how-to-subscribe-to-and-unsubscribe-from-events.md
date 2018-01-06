---
title: "Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5555cc8913bff953601c54aa7430143dc22173c0
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="bd46e-102">Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bd46e-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="bd46e-103">Bu olay ortaya çıktığında çağrılan özel kod yazmanıza istediğinizde, başka bir sınıf tarafından yayımlanan bir olaya abone olun.</span><span class="sxs-lookup"><span data-stu-id="bd46e-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="bd46e-104">Örneğin, bir düğmenin abone `click` uygulamanız kullanıcı düğmesini tıklattığında yararlı bir şeyler yapmak için olay.</span><span class="sxs-lookup"><span data-stu-id="bd46e-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="bd46e-105">Visual Studio IDE kullanarak olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="bd46e-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="bd46e-106">Göremiyorsanız **özellikleri** penceresi, **tasarım** görüntülemek için form veya bir olay işleyicisi oluşturun ve seçmek istediğiniz denetimi sağ **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="bd46e-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="bd46e-107">Üstünde **özellikleri** penceresinde tıklatın **olayları** simgesi.</span><span class="sxs-lookup"><span data-stu-id="bd46e-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="bd46e-108">Örneğin, oluşturmak istediğiniz olayı çift `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="bd46e-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]<span data-ttu-id="bd46e-109">bir boş olay işleyicisi yöntemi oluşturur ve kodunuzu ekler.</span><span class="sxs-lookup"><span data-stu-id="bd46e-109"> creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="bd46e-110">Alternatif olarak, el ile kod ekleyebilirsiniz **kod** görünümü.</span><span class="sxs-lookup"><span data-stu-id="bd46e-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="bd46e-111">Örneğin, aşağıdaki kod satırlarını ne zaman çağrılacağı bir olay işleyicisi yöntemi bildirme `Form` sınıfı başlatır `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="bd46e-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     <span data-ttu-id="bd46e-112">Olaya abone olmak için gerekli kod satırı da otomatik olarak üretildi `InitializeComponent` projenizdeki Form1.Designer.cs dosyasındaki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd46e-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="bd46e-113">Bu benzer:</span><span class="sxs-lookup"><span data-stu-id="bd46e-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="bd46e-114">Program aracılığıyla olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="bd46e-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="bd46e-115">Olayı için temsilci imza, imza eşleşen bir olay işleyicisi yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bd46e-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="bd46e-116">Örneğin, olay dayanıyorsa <xref:System.EventHandler> temsilci türü, aşağıdaki kodu yöntemi saplama temsil eder:</span><span class="sxs-lookup"><span data-stu-id="bd46e-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="bd46e-117">Toplama atama işleci kullanın (`+=`), olay işleyicisi olaya bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="bd46e-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="bd46e-118">Aşağıdaki örnekte, bir nesne adlı varsayın `publisher` sahip adlı bir olay `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="bd46e-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="bd46e-119">Abone sınıfı için olaylarına abone olmak için yayımcı sınıfı başvuru gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd46e-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="bd46e-120">Önceki sözdizimi C# 2. 0'yeni olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bd46e-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="bd46e-121">Tam olarak hangi kapsülleyerek temsilci açıkça oluşturulmalıdır kullanarak C# 1.0 sözdizimi eşdeğerdir `new` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="bd46e-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="bd46e-122">Olay işleyici lambda ifadesi kullanarak da eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="bd46e-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="bd46e-123">Daha fazla bilgi için bkz: [nasıl yapılır: kullanım Lambda ifadeleri dış LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="bd46e-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="bd46e-124">Anonim bir yöntem kullanarak olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="bd46e-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="bd46e-125">Bir olaya daha sonra aboneliği gerekmez, toplama atama işleci kullanabilirsiniz (`+=`) adsız bir yöntem olaya bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="bd46e-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="bd46e-126">Aşağıdaki örnekte, bir nesne adlı varsayın `publisher` sahip adlı bir olay `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfı ayrıca tanımlandı bir tür özel olay bilgilerini taşımak için.</span><span class="sxs-lookup"><span data-stu-id="bd46e-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="bd46e-127">Abone sınıfı bir başvuru gerektiğini unutmayın `publisher` kendi olaylarına abone olmak için.</span><span class="sxs-lookup"><span data-stu-id="bd46e-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="bd46e-128">Kolayca abone adsız bir işlev kullandıysanız bir olaydan aboneliğinizi iptal edilemez olduğunu fark önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bd46e-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="bd46e-129">Bu senaryoda, aboneliğinizi iptal etmek için olaya abone olduğu geri kod, bir temsilci değişkende anonim yöntemi depolamak ve ardından temsilci olaya eklemek gitmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bd46e-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="bd46e-130">Genel olarak, kodunuzda daha sonraki bir noktada olay aboneliğinizi iptal etmek olacaksa olaylarına abone olmak için anonim işlevler kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="bd46e-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="bd46e-131">Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="bd46e-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="bd46e-132">Aboneliği</span><span class="sxs-lookup"><span data-stu-id="bd46e-132">Unsubscribing</span></span>  
 <span data-ttu-id="bd46e-133">Olay ortaya çıktığında çağrılan olay işleyicisi önlemek için olay aboneliği.</span><span class="sxs-lookup"><span data-stu-id="bd46e-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="bd46e-134">Kaynak sızıntıları önlemek için bir abonelik nesnesinin dispose önce olaylarından aboneliği.</span><span class="sxs-lookup"><span data-stu-id="bd46e-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="bd46e-135">Bir olay aboneliği kadar olay yayımlama nesnesindeki altını çizen çok noktaya yayın temsilci abonenin olay işleyicisi yalıtır temsilci bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="bd46e-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="bd46e-136">Bu başvuru yayımlama nesnesi tutar sürece, atık toplama abone nesnenizin silmez.</span><span class="sxs-lookup"><span data-stu-id="bd46e-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="bd46e-137">Bir olay aboneliğinizi iptal etmek için</span><span class="sxs-lookup"><span data-stu-id="bd46e-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="bd46e-138">Çıkarma atama işleci kullanın (`-=`) bir olay aboneliğinizi iptal etmek için:</span><span class="sxs-lookup"><span data-stu-id="bd46e-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="bd46e-139">Tüm aboneler bir olaydan kaldırdınız, yayımcı sınıfı olay örneğinde kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="bd46e-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd46e-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd46e-140">See Also</span></span>  
 [<span data-ttu-id="bd46e-141">Olaylar</span><span class="sxs-lookup"><span data-stu-id="bd46e-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="bd46e-142">event</span><span class="sxs-lookup"><span data-stu-id="bd46e-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)  
 [<span data-ttu-id="bd46e-143">Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama</span><span class="sxs-lookup"><span data-stu-id="bd46e-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [<span data-ttu-id="bd46e-144">-= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bd46e-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="bd46e-145">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="bd46e-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)