---
title: 'Nasıl yapılır: Abone olma ve aboneliği olayları - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 4d06899303110d0b06729f2a02c47b9096bec724
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981809"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="44565-102">Nasıl yapılır: Abone olaylara ve aboneliği kaldırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="44565-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="44565-103">Olay ortaya çıktığında çağrılan özel kod yazmak istediğiniz zaman, başka bir sınıf tarafından yayımlanan bir olaya abone olun.</span><span class="sxs-lookup"><span data-stu-id="44565-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="44565-104">Örneğin, bir düğmenin abone `click` uygulamanızın kullanıcı düğmeye tıkladığında faydalı bir şey yapmak için olay.</span><span class="sxs-lookup"><span data-stu-id="44565-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="44565-105">Visual Studio IDE kullanarak olaylarına abone olma</span><span class="sxs-lookup"><span data-stu-id="44565-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="44565-106">Göremiyorsanız **özellikleri** penceresi içinde **tasarım** görüntülemek için form veya denetim bir olay işleyicisi oluşturun ve istediğiniz sağ **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="44565-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="44565-107">Üst kısmındaki **özellikleri** penceresinde tıklayın **olayları** simgesi.</span><span class="sxs-lookup"><span data-stu-id="44565-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="44565-108">Örneğin, oluşturmak istediğiniz olayı çift `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="44565-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="44565-109">Visual C# boş olay işleyicisi yöntemi oluşturur ve bunu kodunuza ekler.</span><span class="sxs-lookup"><span data-stu-id="44565-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="44565-110">Alternatif olarak, el ile kod ekleyebilirsiniz **kod** görünümü.</span><span class="sxs-lookup"><span data-stu-id="44565-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="44565-111">Örneğin, aşağıdaki kod satırlarını olduğunda çağrılacak olay işleyicisi yöntemi bildirimini `Form` sınıfı harekete geçirirse `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="44565-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="44565-112">Olaya abone için gereken kod satırının, ayrıca otomatik olarak oluşturulan `InitializeComponent` projenizi Form1.Designer.cs dosyasında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44565-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="44565-113">Bunu yeniden birleştirir:</span><span class="sxs-lookup"><span data-stu-id="44565-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="44565-114">Program aracılığıyla olaylarına abone olma</span><span class="sxs-lookup"><span data-stu-id="44565-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="44565-115">Olay için temsilci imzası olan imzayla eşleşen bir olay işleyicisi yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="44565-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="44565-116">Örneğin, olay dayanıyorsa <xref:System.EventHandler> temsilci türü, aşağıdaki kod, metot taslağı temsil eder:</span><span class="sxs-lookup"><span data-stu-id="44565-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="44565-117">Toplama atama işleci kullanın (`+=`), olay işleyicisi olaya bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="44565-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="44565-118">Aşağıdaki örnekte adlı bir nesne olduğunu varsayın `publisher` adlı bir olaya sahip `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="44565-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="44565-119">Abone sınıfı, olaylara abone için bir yayımcı sınıf başvurusu gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44565-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="44565-120">Önceki sözdizimini C# 2.0 sürümünde yeni olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44565-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="44565-121">Tam olarak hangi kapsülleyerek temsilciyi açıkça oluşturulmalıdır kullanarak C# 1.0 söz dizimi eşdeğerdir `new` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="44565-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="44565-122">Bir olay işleyicisi, bir lambda ifadesi kullanılarak da eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="44565-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="44565-123">Daha fazla bilgi için [nasıl yapılır: LINQ dışında lambda ifadeleri kullanma](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="44565-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="44565-124">Anonim bir yöntem kullanarak olaylarına abone olma</span><span class="sxs-lookup"><span data-stu-id="44565-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="44565-125">Daha sonra bir olay aboneliği gerekmez, toplama atama işleci kullanabilirsiniz (`+=`) bir anonim yöntem olaya bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="44565-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="44565-126">Aşağıdaki örnekte adlı bir nesne olduğunu varsayın `publisher` adlı bir olaya sahip `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfı da tanımlanmış bir tür özel olay bilgilerini taşımak için.</span><span class="sxs-lookup"><span data-stu-id="44565-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="44565-127">Abone sınıfı başvuru gerektiğini aklınızda bulundurun `publisher` kendi olaylarına abone olmak için.</span><span class="sxs-lookup"><span data-stu-id="44565-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="44565-128">Abone için anonim bir işlevdir kullandıysanız, kolayca bir olayın aboneliğini kaldırmak olamaz, dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44565-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="44565-129">Bu senaryoda, aboneliğinizi iptal etmek için olaya abone olduğu koda geri, anonim yöntemin bir temsilci değişkende depolamak ve ardından temsilci olaya eklemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44565-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="44565-130">Genel olarak, kodunuza daha sonraki bir noktada olay aboneliği olacaksa olaylarına abone olmak için anonim işlevler kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="44565-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="44565-131">Anonim işlevler hakkında daha fazla bilgi için bkz. [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="44565-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="44565-132">Aboneliği kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="44565-132">Unsubscribing</span></span>  
 <span data-ttu-id="44565-133">Olay işleyicisi, olay ortaya çıktığında çağrılan önlemek için olay aboneliği.</span><span class="sxs-lookup"><span data-stu-id="44565-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="44565-134">Kaynak sızıntılarını önlemek için önce bir abonelik nesnesinin elden olayları aboneliği.</span><span class="sxs-lookup"><span data-stu-id="44565-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="44565-135">Bir olayın aboneliğini kaldırmak kadar olay yayımlama nesnesindeki altını çok noktaya yayın temsilci abonenin olay işleyicisi yalıtan temsilci bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="44565-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="44565-136">Yayımlama nesne, başvuru tutan sürece, atık toplama abone nesnenizin silinmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="44565-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="44565-137">Bir olayın aboneliğini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="44565-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="44565-138">Çıkarma atama işleci kullanın (`-=`) bir olayın aboneliğini kaldırmak için:</span><span class="sxs-lookup"><span data-stu-id="44565-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="44565-139">Bir olayın tüm abonelerine çıktınız, yayımcı sınıf içinde olay örneği kümesine `null`.</span><span class="sxs-lookup"><span data-stu-id="44565-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44565-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44565-140">See also</span></span>

- [<span data-ttu-id="44565-141">Olaylar</span><span class="sxs-lookup"><span data-stu-id="44565-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="44565-142">event</span><span class="sxs-lookup"><span data-stu-id="44565-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)
- [<span data-ttu-id="44565-143">Nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="44565-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="44565-144">-= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="44565-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="44565-145">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="44565-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)
