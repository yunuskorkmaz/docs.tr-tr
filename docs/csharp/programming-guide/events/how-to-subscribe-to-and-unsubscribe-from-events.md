---
title: Etkinliklere abone olunve aboneliğinizi iptal e-Çıkış - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 0a9e2cc64da56c376445efce32e8da36ba9b6cdc
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738228"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="4f57a-102">Etkinliklere abone olunve abonelikten çıkılmaz (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4f57a-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="4f57a-103">Bu olay yükseltildiğinde çağrılan özel kod yazmak istediğinizde başka bir sınıf tarafından yayımlanan bir olaya abone olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="4f57a-104">Örneğin, kullanıcı düğmeyi tıklattığında `click` uygulamanızın yararlı bir şey yapmasını sağlamak için bir düğmenin etkinliğine abone olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="4f57a-105">Visual Studio IDE'yi kullanarak etkinliklere abone olmak için</span><span class="sxs-lookup"><span data-stu-id="4f57a-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="4f57a-106">**Özellikler** penceresini göremiyorsanız, **Tasarım** görünümünde, olay işleyicisi oluşturmak istediğiniz formu veya denetimi sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="4f57a-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="4f57a-107">**Özellikler** penceresinin üstünde, **Etkinlikler** simgesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="4f57a-108">Oluşturmak istediğiniz olayı ( örneğin `Load` olay) çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="4f57a-109">Visual C# boş bir olay işleyicisi yöntemi oluşturur ve kodunuza ekler.</span><span class="sxs-lookup"><span data-stu-id="4f57a-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="4f57a-110">Alternatif olarak **kodu Kod** görünümüne el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="4f57a-111">Örneğin, aşağıdaki kod `Form` satırları, sınıf `Load` olayı yükselttiğinde çağrılacak bir olay işleyicisi yöntemini bildirir.</span><span class="sxs-lookup"><span data-stu-id="4f57a-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="4f57a-112">Etkinliğe abone olmak için gereken kod satırı da projenizdeki `InitializeComponent` Form1.Designer.cs dosyasındaki yöntemde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f57a-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="4f57a-113">Buna benziyor:</span><span class="sxs-lookup"><span data-stu-id="4f57a-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="4f57a-114">Etkinliklere programlı abone olmak için</span><span class="sxs-lookup"><span data-stu-id="4f57a-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="4f57a-115">İmzası olay için temsilci imzasıyla eşleşen bir olay işleyicisi yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="4f57a-116">Örneğin, olay <xref:System.EventHandler> temsilci türünü temel alırsa, aşağıdaki kod yöntem saplamasını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="4f57a-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="4f57a-117">Olay için bir`+=`olay işleyicisi eklemek için ekleme atama işleci ( ) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="4f57a-118">Aşağıdaki örnekte, adlı `publisher` bir nesnenin . `RaiseCustomEvent`adlı bir olayı olduğunu varsayalım</span><span class="sxs-lookup"><span data-stu-id="4f57a-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="4f57a-119">Abone sınıfının etkinliklerine abone olmak için yayımcı sınıfına bir başvuruyapması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="4f57a-120">Önceki sözdiziminin C# 2.0'da yeni olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="4f57a-121">Tam olarak c# 1.0 sözdizimi olan kapsülleme temsilci açıkça `new` anahtar sözcüğü kullanılarak oluşturulmalıdır eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="4f57a-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="4f57a-122">Bir olay işleyicisi belirtmek için [bir lambda ifadesi](../statements-expressions-operators/lambda-expressions.md) de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4f57a-122">You can also use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
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
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="4f57a-123">Anonim bir yöntem kullanarak olaylara abone olmak için</span><span class="sxs-lookup"><span data-stu-id="4f57a-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="4f57a-124">Daha sonra bir etkinliğe aboneliğinizi iptal etmek zorunda kalmazsanız, olaya anonim bir yöntem eklemek için ekleme atama işlecini ()`+=`kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="4f57a-125">Aşağıdaki örnekte, adlı `publisher` bir nesnenin adında `RaiseCustomEvent` bir `CustomEventArgs` olayı olduğunu ve bir sınıfın da bir tür özel olay bilgisi taşımak üzere tanımlandığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4f57a-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="4f57a-126">Abone sınıfının etkinliklerine abone `publisher` olmak için bir başvuruya ihtiyacı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f57a-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="4f57a-127">Abone olmak için anonim bir işlev kullandıysanız, bir etkinlikten kolayca aboneliğinizi kaldıramayacağınızı fark etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4f57a-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="4f57a-128">Bu senaryoda aboneliği iptal etmek için, olaya abone olduğunuz koda geri dönmek, anonim yöntemi bir temsilci değişkeninde depolamak ve ardından temsilciyi olaya eklemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f57a-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="4f57a-129">Genel olarak, kodunuzda daha sonraki bir noktada etkinlikten aboneliğinizi iptal etmek zorunda kalacaksanız, olaylara abone olmak için anonim işlevler kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="4f57a-130">Anonim işlevler hakkında daha fazla bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)</span><span class="sxs-lookup"><span data-stu-id="4f57a-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="4f57a-131">Aboneliği kaldır</span><span class="sxs-lookup"><span data-stu-id="4f57a-131">Unsubscribing</span></span>  
 <span data-ttu-id="4f57a-132">Olay yükseltildiğinde olay işleyicinizin çağrılmasını önlemek için etkinlikten aboneliğinizi iptal edin.</span><span class="sxs-lookup"><span data-stu-id="4f57a-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="4f57a-133">Kaynak sızıntılarını önlemek için, bir abone nesnesini elden çıkarmadan önce olaylardan aboneliğinizi iptal etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="4f57a-134">Bir etkinlikten aboneliğinizi iptal edene kadar, yayımlama nesnesindeki olayın altında yatan çok noktaya yayın temsilcisinin, abonenin olay işleyicisini kapsülleyen temsilciye bir başvurusu vardır.</span><span class="sxs-lookup"><span data-stu-id="4f57a-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="4f57a-135">Yayımlama nesnesi bu başvuruyu tuttuğu sürece, çöp toplama abone nesnenizi silmez.</span><span class="sxs-lookup"><span data-stu-id="4f57a-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="4f57a-136">Bir etkinlikten aboneliğinizi iptal etmek için</span><span class="sxs-lookup"><span data-stu-id="4f57a-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="4f57a-137">Bir olaydan aboneliğini`-=`iptal etmek için çıkarma atama işleci ( ) kullanın:</span><span class="sxs-lookup"><span data-stu-id="4f57a-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="4f57a-138">Tüm aboneler bir etkinlikten aboneliğini iptal ettiğinde, yayımcı sınıfındaki olay örneği `null`.</span><span class="sxs-lookup"><span data-stu-id="4f57a-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f57a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f57a-139">See also</span></span>

- [<span data-ttu-id="4f57a-140">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4f57a-140">Events</span></span>](./index.md)
- [<span data-ttu-id="4f57a-141">Olay</span><span class="sxs-lookup"><span data-stu-id="4f57a-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="4f57a-142">.NET Framework Yönergeleriyle uyumlu olayları yayımlama</span><span class="sxs-lookup"><span data-stu-id="4f57a-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="4f57a-143">- ve -= operatörler</span><span class="sxs-lookup"><span data-stu-id="4f57a-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="4f57a-144">+ ve += işleçleri</span><span class="sxs-lookup"><span data-stu-id="4f57a-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
