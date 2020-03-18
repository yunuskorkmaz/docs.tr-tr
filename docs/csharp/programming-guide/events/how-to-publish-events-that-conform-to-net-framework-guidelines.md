---
title: .NET Framework Yönergelerine Uygun Etkinlikler Nasıl Yayımlanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167547"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="e62c6-102">.NET Framework Yönergelerine Uygun Etkinlikler (C# Programlama Kılavuzu) nasıl yayımlanır?</span><span class="sxs-lookup"><span data-stu-id="e62c6-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="e62c6-103">Aşağıdaki yordam, sınıflarınıza ve yapılarınıza standart .NET Framework deseni izleyen olayların nasıl ekleyeceğinigösterir.</span><span class="sxs-lookup"><span data-stu-id="e62c6-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="e62c6-104">.NET Framework sınıf kitaplığındaki tüm <xref:System.EventHandler> olaylar aşağıdaki gibi tanımlanan temsilciyi temel alar:</span><span class="sxs-lookup"><span data-stu-id="e62c6-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="e62c6-105">.NET Framework 2.0 bu temsilcinin genel <xref:System.EventHandler%601>bir sürümünü sunar.</span><span class="sxs-lookup"><span data-stu-id="e62c6-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="e62c6-106">Aşağıdaki örnekler, her iki sürümün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e62c6-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="e62c6-107">Tanımladığınız sınıflardaki olaylar herhangi bir geçerli temsilci türüne, hatta bir değer döndüren delegelere dayanabilir, ancak aşağıdaki <xref:System.EventHandler>örnekte gösterildiği gibi ,.'ı kullanarak olaylarınızı .NET Framework desenine dayandırdığınız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e62c6-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="e62c6-108">EventHandler deseni dayalı olayları yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="e62c6-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="e62c6-109">(Etkinliğinizle özel veri göndermeniz yoksa bu adımı atlayın ve Adım 3a'ya gidin.) Özel verileriniz için sınıfı hem yayımcınız hem de abone sınıflarınız tarafından görülebilecek bir kapsamda bildirin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="e62c6-110">Ardından, özel etkinlik verilerinizi tutmak için gerekli üyeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="e62c6-111">Bu örnekte, basit bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e62c6-111">In this example, a simple string is returned.</span></span>  
  
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
  
2. <span data-ttu-id="e62c6-112">(Genel sürümünü kullanıyorsanız bu adımı <xref:System.EventHandler%601> atlayın.) Yayımlama sınıfınızda bir temsilci bildirin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="e62c6-113">*EventHandler*ile biten bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="e62c6-114">İkinci parametre özel EventArgs türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e62c6-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="e62c6-115">Aşağıdaki adımlardan birini kullanarak yayımlama sınıfınızdaki olayı bildirin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="e62c6-116">Özel EventArgs sınıfınız yoksa, Etkinlik türünüz genel olmayan EventHandler temsilcisi olur.</span><span class="sxs-lookup"><span data-stu-id="e62c6-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="e62c6-117">C# projenizi oluştururken dahil edilen <xref:System> ad alanında zaten beyan edildiğinden temsilciyi bildirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e62c6-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="e62c6-118">Yayımcı sınıfınıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e62c6-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="e62c6-119">Genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve türetilmiş özel bir <xref:System.EventArgs>sınıfınız varsa, yayımlama sınıfınızın içinde etkinliğinizi bildirin ve 2.</span><span class="sxs-lookup"><span data-stu-id="e62c6-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="e62c6-120">Genel sürümü kullanıyorsanız, özel bir temsilciye ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="e62c6-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="e62c6-121">Bunun yerine, yayımlama sınıfınızda, olay `EventHandler<CustomEventArgs>`türünü açı ayraçları arasında kendi sınıfınızın adını yerine " olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e62c6-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="e62c6-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e62c6-122">Example</span></span>  
 <span data-ttu-id="e62c6-123">Aşağıdaki örnek, özel bir EventArgs sınıfı kullanarak <xref:System.EventHandler%601> ve olay türü olarak önceki adımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="e62c6-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e62c6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e62c6-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="e62c6-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e62c6-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e62c6-126">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e62c6-126">Events</span></span>](./index.md)
- [<span data-ttu-id="e62c6-127">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e62c6-127">Delegates</span></span>](../delegates/index.md)
