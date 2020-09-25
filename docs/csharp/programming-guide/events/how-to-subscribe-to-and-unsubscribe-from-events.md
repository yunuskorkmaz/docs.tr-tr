---
title: Olaylara abone olma ve aboneliği kaldırma-C# Programlama Kılavuzu
description: Olaylara abone olma ve olayları kaldırma hakkında bilgi edinin. Visual Studio IDE 'yi kullanarak, programlı olarak veya anonim bir yöntem kullanarak olaylara abone olun.
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 1e090301982a785fed2a8a6a95ee48bd1c7457ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167489"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="e5106-104">Olaylara abone olma ve aboneliği kaldırma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e5106-104">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>

<span data-ttu-id="e5106-105">Bu olay ortaya çıktığında çağrılan özel kod yazmak istediğinizde, başka bir sınıf tarafından yayımlanan bir olaya abone olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e5106-105">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="e5106-106">Örneğin, `click` Kullanıcı düğmeye tıkladığında uygulamanızı yararlı hale getirmek için bir düğmenin olayına abone olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5106-106">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="e5106-107">Visual Studio IDE kullanarak olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="e5106-107">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="e5106-108">**Özellikler** penceresini göremiyorsanız, **Tasarım** görünümü ' nde, olay işleyicisi oluşturmak istediğiniz form veya denetime sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e5106-108">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="e5106-109">**Özellikler** penceresinin üstünde **Olaylar** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-109">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="e5106-110">Oluşturmak istediğiniz olaya çift tıklayın, örneğin `Load` olay.</span><span class="sxs-lookup"><span data-stu-id="e5106-110">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="e5106-111">Visual C# boş bir olay işleyici yöntemi oluşturur ve bunu kodunuza ekler.</span><span class="sxs-lookup"><span data-stu-id="e5106-111">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="e5106-112">Alternatif olarak, **Kod görünümünde kodu el ile de ekleyebilirsiniz** .</span><span class="sxs-lookup"><span data-stu-id="e5106-112">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="e5106-113">Örneğin, aşağıdaki kod satırları, `Form` sınıf olayı harekete geçirirse çağrılacak bir olay işleyicisi yöntemi bildirir `Load` .</span><span class="sxs-lookup"><span data-stu-id="e5106-113">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="e5106-114">Olaya abone olmak için gereken kod satırı, `InitializeComponent` projenizdeki Form1.Designer.cs dosyasındaki yönteminde de otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e5106-114">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="e5106-115">Şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="e5106-115">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="e5106-116">Olaylara programlı bir şekilde abone olmak için</span><span class="sxs-lookup"><span data-stu-id="e5106-116">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="e5106-117">İmzası, olayın temsilci imzasıyla eşleşen bir olay işleyici yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-117">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="e5106-118">Örneğin, olay <xref:System.EventHandler> temsilci türünü temel alıyorsa, aşağıdaki kod yöntem saplaması ' nı temsil eder:</span><span class="sxs-lookup"><span data-stu-id="e5106-118">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="e5106-119">`+=`Olaya bir olay işleyicisi iliştirmek için ekleme atama işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5106-119">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="e5106-120">Aşağıdaki örnekte adlı bir nesnesinin adlı bir olayı olduğunu varsayalım `publisher` `RaiseCustomEvent` .</span><span class="sxs-lookup"><span data-stu-id="e5106-120">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="e5106-121">Abone sınıfının olaylarına abone olmak için yayımcı sınıfına bir başvuru ihtiyacı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-121">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="e5106-122">Önceki sözdiziminin C# 2,0 ' de yeni olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-122">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="e5106-123">Bu, kapsülleme temsilcisinin anahtar sözcüğü kullanılarak açıkça oluşturulması gereken C# 1,0 sözdizimine tam olarak eşdeğerdir `new` :</span><span class="sxs-lookup"><span data-stu-id="e5106-123">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="e5106-124">Bir olay işleyicisi belirtmek için bir [lambda ifadesi](../../language-reference/operators/lambda-expressions.md) de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e5106-124">You can also use a [lambda expression](../../language-reference/operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="e5106-125">Anonim bir yöntem kullanarak olaylara abone olma</span><span class="sxs-lookup"><span data-stu-id="e5106-125">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="e5106-126">Bir olayı daha sonra kaldırmak zorunda değilseniz, `+=` olaya anonim bir yöntem iliştirmek için ekleme atama işlecini () kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5106-126">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="e5106-127">Aşağıdaki örnekte, adlı bir nesnesinin adlı bir olayı olduğunu `publisher` `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfın bir tür özel olay bilgilerini taşımak için de tanımlandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e5106-127">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="e5106-128">Abone sınıfının `publisher` olaylarına abone olmak için bir başvuruya ihtiyacı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-128">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="e5106-129">Abone olmak için anonim bir işlev kullandıysanız, bir olaydan kolayca abonelik yapamayacağını fark etmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e5106-129">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="e5106-130">Bu senaryoda aboneliğinizi kaldırmak için, olaya abone olduğunuz koda geri dönmek, anonim yöntemi bir temsilci değişkeninde depolamak ve ardından temsilciyi olaya eklemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5106-130">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="e5106-131">Genel olarak, kodunuzda daha sonraki bir noktada olay aboneliğinizi kaldırmak zorunda olmanız durumunda olaylara abone olmak için anonim işlevler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e5106-131">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="e5106-132">Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e5106-132">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="e5106-133">Aboneliği kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="e5106-133">Unsubscribing</span></span>  

 <span data-ttu-id="e5106-134">Olay işleyicinizin olay ortaya çıktığında çağrılmasını engellemek için, olaydan aboneliği kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e5106-134">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="e5106-135">Kaynak sızıntılarını engellemek için, bir abone nesnesini atmadan önce etkinliklerden aboneliğinizi iptal etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e5106-135">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="e5106-136">Bir olaydan abonelik aboneliğini kaldırana kadar, yayımlama nesnesindeki olayı oluşturan çok noktaya yayın temsilcisi, abonenin olay işleyicisini kapsülleyen temsilciye bir başvuruya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e5106-136">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="e5106-137">Yayımlama nesnesi bu başvuruyu taşıdığı sürece çöp toplama işlemi abone nesneniz silinmez.</span><span class="sxs-lookup"><span data-stu-id="e5106-137">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="e5106-138">Bir olaydan aboneliğinizi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="e5106-138">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="e5106-139">`-=`Bir olaydan aboneliğinizi kaldırmak için çıkarma atama işlecini () kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5106-139">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="e5106-140">Tüm aboneler bir olaydan aboneliği kaldırdığınızda, yayımcı sınıfındaki olay örneği olarak ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="e5106-140">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5106-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5106-141">See also</span></span>

- [<span data-ttu-id="e5106-142">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e5106-142">Events</span></span>](./index.md)
- [<span data-ttu-id="e5106-143">olay</span><span class="sxs-lookup"><span data-stu-id="e5106-143">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="e5106-144">.NET Kılavuzlarına uygun olaylar yayımlama</span><span class="sxs-lookup"><span data-stu-id="e5106-144">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="e5106-145">-ve-= işleçleri</span><span class="sxs-lookup"><span data-stu-id="e5106-145">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="e5106-146">+ ve + = işleçleri</span><span class="sxs-lookup"><span data-stu-id="e5106-146">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
