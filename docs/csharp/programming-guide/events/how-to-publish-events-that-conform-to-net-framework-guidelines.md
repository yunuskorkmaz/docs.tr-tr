---
title: 'Nasıl yapılır: .NET Framework yönergeleri- C# programlama kılavuzuna uygun olan olayları yayımlayın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 93924638fabe9a46af39006130d4f07de2ad0541
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590486"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="64371-102">Nasıl yapılır: .NET Framework yönergelerine uygun olan olayları yayımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="64371-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="64371-103">Aşağıdaki yordam, sınıflarınıza ve yapılarına standart .NET Framework modelini izleyen olayların nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="64371-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="64371-104">.NET Framework sınıf kitaplığındaki tüm olaylar, aşağıdaki şekilde tanımlanan <xref:System.EventHandler> temsilciyi temel alır:</span><span class="sxs-lookup"><span data-stu-id="64371-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="64371-105">.NET Framework 2,0, bu temsilcinin <xref:System.EventHandler%601>genel bir sürümünü sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64371-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="64371-106">Aşağıdaki örneklerde her iki sürümün de nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64371-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="64371-107">Tanımladığınız sınıflardaki olaylar geçerli temsilci türlerini temel alabilir, hatta bir değer döndüren temsilciler olsa da, aşağıdaki örnekte gösterildiği gibi, kullanarak <xref:System.EventHandler>olaylarınızın .NET Framework düzeniyle temel almanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="64371-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="64371-108">Olayları EventHandler düzenine göre yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="64371-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="64371-109">(Bu adımı atlayın ve olaylarınız ile özel veriler göndermeniz gerekmez. adıma gidin.) Özel verilerinize ait sınıfı, hem Yayımcı hem de abone sınıflarınızda görünen bir kapsamda bildirin.</span><span class="sxs-lookup"><span data-stu-id="64371-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="64371-110">Ardından, özel olay verilerinizi tutmak için gerekli üyeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64371-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="64371-111">Bu örnekte basit bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="64371-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2. <span data-ttu-id="64371-112">(Genel sürümünü <xref:System.EventHandler%601> kullanıyorsanız bu adımı atlayın.) Yayımlama sınıfınıza bir temsilci bildirin.</span><span class="sxs-lookup"><span data-stu-id="64371-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="64371-113">Buna *EventHandler*ile biten bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="64371-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="64371-114">İkinci parametre özel EventArgs türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="64371-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="64371-115">Aşağıdaki adımlardan birini kullanarak, yayımlama sınıfınıza olayı bildirin.</span><span class="sxs-lookup"><span data-stu-id="64371-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="64371-116">Özel EventArgs sınıfınız yoksa, olay türü genel olmayan EventHandler temsilcisi olur.</span><span class="sxs-lookup"><span data-stu-id="64371-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="64371-117">Projenizi oluştururken dahil edilen <xref:System> ad alanında zaten bildirildiği için temsilciyi bildirmeniz gerekmez. C#</span><span class="sxs-lookup"><span data-stu-id="64371-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="64371-118">Aşağıdaki kodu Publisher sınıfınıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64371-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="64371-119">Öğesinin <xref:System.EventHandler> genel olmayan sürümünü kullanıyorsanız ve öğesinden <xref:System.EventArgs>türetilmiş özel bir sınıfınız varsa, bu kodunuzu yayımlama sınıfınız içinde bildirin ve 2. adımdaki temsilcinizi tür olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="64371-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="64371-120">Genel sürümü kullanıyorsanız özel bir temsilciye ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="64371-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="64371-121">Bunun yerine, yayımlama sınıfınız içinde, kendi sınıfınızın adını açılı ayraçlar arasında `EventHandler<CustomEventArgs>`değiştirerek olay türü olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64371-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="64371-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="64371-122">Example</span></span>  
 <span data-ttu-id="64371-123">Aşağıdaki örnek, bir özel EventArgs sınıfı ve <xref:System.EventHandler%601> olay türü olarak önceki adımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="64371-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="64371-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64371-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="64371-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="64371-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="64371-126">Olaylar</span><span class="sxs-lookup"><span data-stu-id="64371-126">Events</span></span>](./index.md)
- [<span data-ttu-id="64371-127">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="64371-127">Delegates</span></span>](../delegates/index.md)
