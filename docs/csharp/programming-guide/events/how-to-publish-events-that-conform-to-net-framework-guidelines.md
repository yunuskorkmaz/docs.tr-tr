---
title: "Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 570729e432146b4ef97e4c487f644b12b354bb4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="e49a8-102">Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e49a8-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="e49a8-103">Aşağıdaki yordam standarda olayları ekleneceği gösterilmektedir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıflar ve yapılar deseni.</span><span class="sxs-lookup"><span data-stu-id="e49a8-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="e49a8-104">Tüm olaylar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı temel <xref:System.EventHandler> temsilci, hangi şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="e49a8-104">All events in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="e49a8-105">[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Bu temsilci genel bir sürümünü kullanıma sunmaktadır <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="e49a8-105">The [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="e49a8-106">Aşağıdaki örnekler, her iki sürümünü de kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e49a8-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="e49a8-107">Tanımladığınız sınıflarda olayları herhangi geçerli temsilci türü, bir değer döndürmesi bile temsilciler dayalı olabilir ancak genellikle için olaylarınızı temel önerilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kullanarak düzeni <xref:System.EventHandler>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e49a8-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="e49a8-108">EventHandler deseni temel alınarak olayları yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="e49a8-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="e49a8-109">(Bu adımı atlayın ve, olay ile özel verileri göndermek yoksa adım 3a gidin.) Özel verilerinizi yayımcısı ve abonesi sınıflarına görünür bir kapsamda için sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="e49a8-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="e49a8-110">Ardından, özel olay verilerini tutacak gerekli üyeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e49a8-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="e49a8-111">Bu örnekte, basit bir dize döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e49a8-111">In this example, a simple string is returned.</span></span>  
  
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
  
2.  <span data-ttu-id="e49a8-112">(Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Bir temsilci yayımlama sınıfınızda bildirin.</span><span class="sxs-lookup"><span data-stu-id="e49a8-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="e49a8-113">İle biten bir ad verin *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="e49a8-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="e49a8-114">İkinci parametre, özel EventArgs türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e49a8-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="e49a8-115">Olay yayımlama sınıfınızda aşağıdaki adımlardan birini kullanarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="e49a8-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="e49a8-116">Olay türü özel bir EventArgs sınıf varsa, genel olmayan OlayÝþleyicisi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e49a8-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="e49a8-117">İçinde zaten bildirildiğinden temsilci bildirme gerekmez <xref:System> C# projenize oluşturduğunuzda, dahil edilen ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e49a8-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="e49a8-118">Yayımcı sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e49a8-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="e49a8-119">Genel olmayan sürümünü kullanıyorsanız, <xref:System.EventHandler> ve türetilen özel bir sınıf sahip <xref:System.EventArgs>, yayımlama sınıfınız içindeki, olay bildirme ve 2. adımda, temsilci türü olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e49a8-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="e49a8-120">Genel sürümünü kullanıyorsanız, özel bir temsilci gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e49a8-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="e49a8-121">Bunun yerine, yayımlama sınıfınızda olay türü olarak belirttiğiniz `EventHandler<CustomEventArgs>`, köşeli parantez arasında kendi sınıfın adını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="e49a8-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="e49a8-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e49a8-122">Example</span></span>  
 <span data-ttu-id="e49a8-123">Aşağıdaki örnek, özel bir EventArgs sınıf kullanarak önceki adımları gösterir ve <xref:System.EventHandler%601> olay türü.</span><span class="sxs-lookup"><span data-stu-id="e49a8-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e49a8-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e49a8-124">See Also</span></span>  
 <xref:System.Delegate>  
 [<span data-ttu-id="e49a8-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e49a8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e49a8-126">Olayları</span><span class="sxs-lookup"><span data-stu-id="e49a8-126">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="e49a8-127">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e49a8-127">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
