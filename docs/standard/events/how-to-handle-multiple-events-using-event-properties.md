---
title: 'Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme'
description: Olay özelliklerini kullanarak çok sayıda olayı nasıl işleyeceğinizi öğrenin. Temsilci koleksiyonları, olay anahtarlarını & olay özelliklerini tanımlayın. Add & Remove erişimcisi yöntemlerini uygulayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET]
- multiple events [.NET]
- event handling [.NET], with multiple events
- events [.NET], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: 2f2cd2d17df6d4bbbdaec09be27f8e74367d2bcb
ms.sourcegitcommit: 652f62fc8f3ab6a264681b6eb5211ac7539bd115
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105964786"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="e16d9-105">Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="e16d9-105">How to: Handle Multiple Events Using Event Properties</span></span>

<span data-ttu-id="e16d9-106">Olay özelliklerini kullanmak için olayları oluşturan sınıftaki olay özelliklerini tanımlayın ve ardından olayları işleyen sınıflardaki olay özellikleri için temsilcileri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-106">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="e16d9-107">Bir sınıfta birden çok olay özelliği uygulamak için sınıfı, her olay için tanımlanan temsilciyi dahili olarak depolayıp sürdürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e16d9-107">To implement multiple event properties in a class, the class should internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="e16d9-108">Her alan-benzeri olay için, karşılık gelen bir yedekleme alanı başvuru türü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e16d9-108">For each field-like-event, a corresponding backing-field reference type is generated.</span></span> <span data-ttu-id="e16d9-109">Bu, olayların sayısı arttıkça gereksiz ayırmaya yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="e16d9-109">This can lead to unnecessary allocations when the number of events increases.</span></span> <span data-ttu-id="e16d9-110">Alternatif olarak, <xref:System.ComponentModel.EventHandlerList> olayları anahtara göre depolayan ortak bir yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="e16d9-110">As an alternative, a common approach is to maintain an <xref:System.ComponentModel.EventHandlerList> which stores events by key.</span></span>
  
 <span data-ttu-id="e16d9-111">Her bir olay için temsilcileri depolamak amacıyla <xref:System.ComponentModel.EventHandlerList> sınıfını kullanabilirsiniz ya da kendi koleksiyonunuzu uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e16d9-111">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="e16d9-112">Koleksiyon sınıfı olay anahtarına bağlı olarak ayarlama, erişme ve olay işleyici temsilcisini almak için yöntemler sağlamak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="e16d9-112">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="e16d9-113">Örneğin, bir <xref:System.Collections.Hashtable> sınıfı kullanabilir veya <xref:System.Collections.DictionaryBase> sınıfından özel bir sınıf türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e16d9-113">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="e16d9-114">Temsilci koleksiyonuna ait uygulama detaylarının sınıfınızın dışında sunulmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e16d9-114">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="e16d9-115">Sınıf içindeki her bir olay özelliği, bir ekleme erişimci yöntemi ve bir kaldırma erişimci yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e16d9-115">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="e16d9-116">Bir olay özelliğine ait ekleme erişimcisi girdi temsilci örneğini temsilci koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="e16d9-116">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="e16d9-117">Bir olay özelliğine ait kaldırma erişimcisi girdi temsilci örneğini temsilci koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e16d9-117">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="e16d9-118">Olay özellik erişimcileri, örnekleri temsilci koleksiyona eklemek veya kaldırmak için olay özelliği için önceden tanımlanmış anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e16d9-118">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="e16d9-119">Olay özelliklerini kullanarak birden çok olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="e16d9-119">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="e16d9-120">Olayları oluşturan sınıf içinde bir temsilci koleksiyon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-120">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="e16d9-121">Her bir olay için bir anahtar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-121">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="e16d9-122">Olayları oluşturan sınıftaki olay özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-122">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="e16d9-123">Olay özelliklerine ait ekleme ve kaldırma erişimci yöntemlerini uygulamak için temsilci koleksiyonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-123">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="e16d9-124">Olayları işleyen sınıflardaki olay işleyici temsilcilerini eklemek ve kaldırmak için ortak olay özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e16d9-124">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e16d9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e16d9-125">Example</span></span>  

 <span data-ttu-id="e16d9-126">Aşağıdaki C# örneği her bir olay temsilcisini depolamak için bir `MouseDown` kullanarak `MouseUp` ve <xref:System.ComponentModel.EventHandlerList> olay özelliklerini uygular.</span><span class="sxs-lookup"><span data-stu-id="e16d9-126">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="e16d9-127">Olay özellik yapılarının anahtar kelimeleri kalın yazı tipindedir.</span><span class="sxs-lookup"><span data-stu-id="e16d9-127">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="e16d9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e16d9-128">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="e16d9-129">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="e16d9-129">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e16d9-130">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="e16d9-130">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
