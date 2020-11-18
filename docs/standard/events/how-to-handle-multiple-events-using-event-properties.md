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
ms.openlocfilehash: c62073e26ff0831bb582c9e64c16b7ec7c05b26e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828381"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="554ce-105">Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="554ce-105">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="554ce-106">Olay özelliklerini kullanmak için olayları oluşturan sınıftaki olay özelliklerini tanımlayın ve ardından olayları işleyen sınıflardaki olay özellikleri için temsilcileri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="554ce-106">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="554ce-107">Bir sınıfta birden çok olay özelliğini uygulamak amacıyla sınıfın, her bir olay için tanımlanan temsilciyi dahili olarak depolaması ve koruması gerekir.</span><span class="sxs-lookup"><span data-stu-id="554ce-107">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="554ce-108">Bir olay anahtarı tarafından dizinlenen bir temsilci koleksiyonunun uygulanması tipik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="554ce-108">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="554ce-109">Her bir olay için temsilcileri depolamak amacıyla <xref:System.ComponentModel.EventHandlerList> sınıfını kullanabilirsiniz ya da kendi koleksiyonunuzu uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="554ce-109">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="554ce-110">Koleksiyon sınıfı olay anahtarına bağlı olarak ayarlama, erişme ve olay işleyici temsilcisini almak için yöntemler sağlamak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="554ce-110">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="554ce-111">Örneğin, bir <xref:System.Collections.Hashtable> sınıfı kullanabilir veya <xref:System.Collections.DictionaryBase> sınıfından özel bir sınıf türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="554ce-111">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="554ce-112">Temsilci koleksiyonuna ait uygulama detaylarının sınıfınızın dışında sunulmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="554ce-112">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="554ce-113">Sınıf içindeki her bir olay özelliği, bir ekleme erişimci yöntemi ve bir kaldırma erişimci yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="554ce-113">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="554ce-114">Bir olay özelliğine ait ekleme erişimcisi girdi temsilci örneğini temsilci koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="554ce-114">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="554ce-115">Bir olay özelliğine ait kaldırma erişimcisi girdi temsilci örneğini temsilci koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="554ce-115">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="554ce-116">Olay özellik erişimcileri, örnekleri temsilci koleksiyona eklemek veya kaldırmak için olay özelliği için önceden tanımlanmış anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="554ce-116">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="554ce-117">Olay özelliklerini kullanarak birden çok olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="554ce-117">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="554ce-118">Olayları oluşturan sınıf içinde bir temsilci koleksiyon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="554ce-118">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="554ce-119">Her bir olay için bir anahtar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="554ce-119">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="554ce-120">Olayları oluşturan sınıftaki olay özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="554ce-120">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="554ce-121">Olay özelliklerine ait ekleme ve kaldırma erişimci yöntemlerini uygulamak için temsilci koleksiyonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="554ce-121">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="554ce-122">Olayları işleyen sınıflardaki olay işleyici temsilcilerini eklemek ve kaldırmak için ortak olay özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="554ce-122">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="554ce-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="554ce-123">Example</span></span>  
 <span data-ttu-id="554ce-124">Aşağıdaki C# örneği her bir olay temsilcisini depolamak için bir `MouseDown` kullanarak `MouseUp` ve <xref:System.ComponentModel.EventHandlerList> olay özelliklerini uygular.</span><span class="sxs-lookup"><span data-stu-id="554ce-124">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="554ce-125">Olay özellik yapılarının anahtar kelimeleri kalın yazı tipindedir.</span><span class="sxs-lookup"><span data-stu-id="554ce-125">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="554ce-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="554ce-126">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="554ce-127">Olaylar</span><span class="sxs-lookup"><span data-stu-id="554ce-127">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="554ce-128">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="554ce-128">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
