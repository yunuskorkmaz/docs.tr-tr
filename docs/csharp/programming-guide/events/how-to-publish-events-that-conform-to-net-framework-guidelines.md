---
title: .NET yönergeleriyle uyumlu olayları yayımlama-C# Programlama Kılavuzu
description: .NET yönergelerine uygun olan olayları yayımlamayı öğrenin. .NET sınıf kitaplığındaki tüm olaylar EventHandler temsilcisini temel alır.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cc8b0a9fdaeeb6ab6290630c5d78044c2696b9a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466176"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="5bc55-104">.NET yönergeleriyle uyumlu olayları yayımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5bc55-104">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="5bc55-105">Aşağıdaki yordamda, sınıflarınıza ve yapılarına standart .NET modelini izleyen olayların nasıl ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5bc55-105">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="5bc55-106">.NET sınıf kitaplığındaki tüm olaylar <xref:System.EventHandler> , aşağıdaki şekilde tanımlanan temsilciyi temel alır:</span><span class="sxs-lookup"><span data-stu-id="5bc55-106">All events in the .NET class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="5bc55-107">.NET Framework 2,0, bu temsilcinin genel bir sürümünü sunmaktadır <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="5bc55-107">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="5bc55-108">Aşağıdaki örneklerde her iki sürümün de nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5bc55-108">The following examples show how to use both versions.</span></span>

<span data-ttu-id="5bc55-109">Tanımladığınız sınıflardaki olaylar geçerli temsilci türlerini temel alabilir, hatta bir değer döndüren temsilciler bile, <xref:System.EventHandler> Aşağıdaki örnekte gösterildiği gibi kullanarak olaylarınızı .net düzenine dayandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="5bc55-109">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="5bc55-110">Bu ad, `EventHandler` olayı gerçekten işlemediği için bir karışıklığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5bc55-110">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="5bc55-111"><xref:System.EventHandler>, Ve genel <xref:System.EventHandler%601> temsilci türleridir.</span><span class="sxs-lookup"><span data-stu-id="5bc55-111">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="5bc55-112">İmza, temsilci tanımıyla eşleşen bir yöntem veya lambda ifadesi *olay işleyicisidir* ve olay harekete çıktığında çağrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="5bc55-112">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="5bc55-113">Etkinlik, EventHandler düzenine göre yayımlayın</span><span class="sxs-lookup"><span data-stu-id="5bc55-113">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="5bc55-114">(Bu adımı atlayın ve olaylarınız ile özel veriler göndermeniz gerekmez. adıma gidin.) Özel verilerinize ait sınıfı, hem Yayımcı hem de abone sınıflarınızda görünen bir kapsamda bildirin.</span><span class="sxs-lookup"><span data-stu-id="5bc55-114">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="5bc55-115">Ardından, özel olay verilerinizi tutmak için gerekli üyeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bc55-115">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="5bc55-116">Bu örnekte basit bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5bc55-116">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="5bc55-117">(Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Yayımlama sınıfınıza bir temsilci bildirin.</span><span class="sxs-lookup"><span data-stu-id="5bc55-117">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="5bc55-118">İle biten bir ad verin `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="5bc55-118">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="5bc55-119">İkinci parametre özel `EventArgs` türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bc55-119">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="5bc55-120">Aşağıdaki adımlardan birini kullanarak, yayımlama sınıfınıza olayı bildirin.</span><span class="sxs-lookup"><span data-stu-id="5bc55-120">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="5bc55-121">Özel EventArgs sınıfınız yoksa, olay türü genel olmayan EventHandler temsilcisi olur.</span><span class="sxs-lookup"><span data-stu-id="5bc55-121">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="5bc55-122"><xref:System>C# projenizi oluştururken dahil edilen ad alanında zaten bildirildiği için temsilciyi bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5bc55-122">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="5bc55-123">Aşağıdaki kodu Publisher sınıfınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bc55-123">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="5bc55-124">Öğesinin genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve öğesinden türetilmiş özel bir sınıfınız varsa, bu kodunuzu <xref:System.EventArgs> Yayımlama sınıfınız içinde bildirin ve 2. adımdaki temsilcinizi tür olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="5bc55-124">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="5bc55-125">Genel sürümü kullanıyorsanız özel bir temsilciye ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="5bc55-125">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="5bc55-126">Bunun yerine, yayımlama sınıfınız içinde, `EventHandler<CustomEventArgs>` kendi sınıfınızın adını açılı ayraçlar arasında değiştirerek olay türü olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bc55-126">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="5bc55-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bc55-127">Example</span></span>

<span data-ttu-id="5bc55-128">Aşağıdaki örnek, bir özel EventArgs sınıfı ve olay türü olarak önceki adımları gösterir <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="5bc55-128">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="5bc55-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bc55-129">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="5bc55-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5bc55-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bc55-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="5bc55-131">Events</span></span>](index.md)
- [<span data-ttu-id="5bc55-132">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5bc55-132">Delegates</span></span>](../delegates/index.md)
