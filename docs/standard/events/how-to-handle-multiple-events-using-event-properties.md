---
title: 'Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme'
description: Olay özelliklerini kullanarak çok sayıda olayı nasıl işleyeceğinizi öğrenin. Temsilci koleksiyonları, olay anahtarlarını & olay özelliklerini tanımlayın. Add & Remove erişimcisi yöntemlerini uygulayın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: 5b528aa2145ba703ce605ce22ae7d643f1e5b8d0
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769021"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="a7c1d-105">Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="a7c1d-105">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="a7c1d-106">Olay özelliklerini kullanmak için olayları oluşturan sınıftaki olay özelliklerini tanımlayın ve ardından olayları işleyen sınıflardaki olay özellikleri için temsilcileri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-106">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="a7c1d-107">Bir sınıfta birden çok olay özelliğini uygulamak amacıyla sınıfın, her bir olay için tanımlanan temsilciyi dahili olarak depolaması ve koruması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-107">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="a7c1d-108">Bir olay anahtarı tarafından dizinlenen bir temsilci koleksiyonunun uygulanması tipik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-108">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="a7c1d-109">Her bir olay için temsilcileri depolamak amacıyla <xref:System.ComponentModel.EventHandlerList> sınıfını kullanabilirsiniz ya da kendi koleksiyonunuzu uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-109">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="a7c1d-110">Koleksiyon sınıfı olay anahtarına bağlı olarak ayarlama, erişme ve olay işleyici temsilcisini almak için yöntemler sağlamak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-110">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="a7c1d-111">Örneğin, bir <xref:System.Collections.Hashtable> sınıfı kullanabilir veya <xref:System.Collections.DictionaryBase> sınıfından özel bir sınıf türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-111">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="a7c1d-112">Temsilci koleksiyonuna ait uygulama detaylarının sınıfınızın dışında sunulmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-112">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="a7c1d-113">Sınıf içindeki her bir olay özelliği, bir ekleme erişimci yöntemi ve bir kaldırma erişimci yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-113">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="a7c1d-114">Bir olay özelliğine ait ekleme erişimcisi girdi temsilci örneğini temsilci koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-114">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="a7c1d-115">Bir olay özelliğine ait kaldırma erişimcisi girdi temsilci örneğini temsilci koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-115">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="a7c1d-116">Olay özellik erişimcileri, örnekleri temsilci koleksiyona eklemek veya kaldırmak için olay özelliği için önceden tanımlanmış anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-116">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="a7c1d-117">Olay özelliklerini kullanarak birden çok olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="a7c1d-117">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="a7c1d-118">Olayları oluşturan sınıf içinde bir temsilci koleksiyon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-118">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="a7c1d-119">Her bir olay için bir anahtar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-119">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="a7c1d-120">Olayları oluşturan sınıftaki olay özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-120">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="a7c1d-121">Olay özelliklerine ait ekleme ve kaldırma erişimci yöntemlerini uygulamak için temsilci koleksiyonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-121">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="a7c1d-122">Olayları işleyen sınıflardaki olay işleyici temsilcilerini eklemek ve kaldırmak için ortak olay özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-122">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7c1d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7c1d-123">Example</span></span>  
 <span data-ttu-id="a7c1d-124">Aşağıdaki C# örneği her bir olay temsilcisini depolamak için bir `MouseDown` kullanarak `MouseUp` ve <xref:System.ComponentModel.EventHandlerList> olay özelliklerini uygular.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-124">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="a7c1d-125">Olay özellik yapılarının anahtar kelimeleri kalın yazı tipindedir.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-125">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="a7c1d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c1d-126">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="a7c1d-127">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="a7c1d-127">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a7c1d-128">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="a7c1d-128">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
