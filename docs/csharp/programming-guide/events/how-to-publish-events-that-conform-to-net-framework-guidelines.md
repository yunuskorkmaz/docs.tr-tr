---
title: .NET Framework yönergeleri ile uyumlu olayları yayımlama-C# Programlama Kılavuzu
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144805"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="639ed-102">.NET Framework yönergelerine uygun olayları yayımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="639ed-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="639ed-103">Aşağıdaki yordam, sınıflarınıza ve yapılarına standart .NET Framework modelini izleyen olayların nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="639ed-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="639ed-104">.NET Framework sınıf kitaplığındaki tüm olaylar <xref:System.EventHandler> , aşağıdaki şekilde tanımlanan temsilciyi temel alır:</span><span class="sxs-lookup"><span data-stu-id="639ed-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="639ed-105">.NET Framework 2,0, bu temsilcinin genel bir sürümünü sunmaktadır <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="639ed-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="639ed-106">Aşağıdaki örneklerde her iki sürümün de nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="639ed-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="639ed-107">Tanımladığınız sınıflardaki olaylar geçerli temsilci türlerini temel alabilir, hatta bir değer döndüren temsilciler olsa da, <xref:System.EventHandler> Aşağıdaki örnekte gösterildiği gibi, kullanarak olaylarınızın .NET Framework düzeniyle temel almanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="639ed-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="639ed-108">Bu ad, `EventHandler` olayı gerçekten işlemediği için bir karışıklığına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="639ed-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="639ed-109"><xref:System.EventHandler>, Ve genel <xref:System.EventHandler%601> temsilci türleridir.</span><span class="sxs-lookup"><span data-stu-id="639ed-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="639ed-110">İmza, temsilci tanımıyla eşleşen bir yöntem veya lambda ifadesi *olay işleyicisidir* ve olay harekete çıktığında çağrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="639ed-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="639ed-111">Olayları EventHandler düzenine göre yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="639ed-111">To publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="639ed-112">(Bu adımı atlayın ve olaylarınız ile özel veriler göndermeniz gerekmez. adıma gidin.) Özel verilerinize ait sınıfı, hem Yayımcı hem de abone sınıflarınızda görünen bir kapsamda bildirin.</span><span class="sxs-lookup"><span data-stu-id="639ed-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="639ed-113">Ardından, özel olay verilerinizi tutmak için gerekli üyeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="639ed-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="639ed-114">Bu örnekte basit bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="639ed-114">In this example, a simple string is returned.</span></span>

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

2. <span data-ttu-id="639ed-115">(Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Yayımlama sınıfınıza bir temsilci bildirin.</span><span class="sxs-lookup"><span data-stu-id="639ed-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="639ed-116">İle biten bir ad verin `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="639ed-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="639ed-117">İkinci parametre özel `EventArgs` türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="639ed-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="639ed-118">Aşağıdaki adımlardan birini kullanarak, yayımlama sınıfınıza olayı bildirin.</span><span class="sxs-lookup"><span data-stu-id="639ed-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="639ed-119">Özel EventArgs sınıfınız yoksa, olay türü genel olmayan EventHandler temsilcisi olur.</span><span class="sxs-lookup"><span data-stu-id="639ed-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="639ed-120"><xref:System>C# projenizi oluştururken dahil edilen ad alanında zaten bildirildiği için temsilciyi bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="639ed-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="639ed-121">Aşağıdaki kodu Publisher sınıfınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="639ed-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="639ed-122">Öğesinin genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve öğesinden türetilmiş özel bir sınıfınız varsa, bu kodunuzu <xref:System.EventArgs> Yayımlama sınıfınız içinde bildirin ve 2. adımdaki temsilcinizi tür olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="639ed-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="639ed-123">Genel sürümü kullanıyorsanız özel bir temsilciye ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="639ed-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="639ed-124">Bunun yerine, yayımlama sınıfınız içinde, `EventHandler<CustomEventArgs>` kendi sınıfınızın adını açılı ayraçlar arasında değiştirerek olay türü olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="639ed-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="639ed-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="639ed-125">Example</span></span>

<span data-ttu-id="639ed-126">Aşağıdaki örnek, bir özel EventArgs sınıfı ve olay türü olarak önceki adımları gösterir <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="639ed-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="639ed-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="639ed-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="639ed-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="639ed-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="639ed-129">Olaylar</span><span class="sxs-lookup"><span data-stu-id="639ed-129">Events</span></span>](index.md)
- [<span data-ttu-id="639ed-130">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="639ed-130">Delegates</span></span>](../delegates/index.md)
