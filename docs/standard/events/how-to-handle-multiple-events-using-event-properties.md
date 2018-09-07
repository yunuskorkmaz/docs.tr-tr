---
title: 'Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e16270fd900c1c786cfd74f484455481d91e5b52
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076391"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="25cda-102">Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="25cda-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="25cda-103">Olay özelliklerini kullanmak için olayları oluşturan sınıftaki olay özelliklerini tanımlayın ve ardından olayları işleyen sınıflardaki olay özellikleri için temsilcileri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="25cda-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="25cda-104">Bir sınıfta birden çok olay özelliğini uygulamak amacıyla sınıfın, her bir olay için tanımlanan temsilciyi dahili olarak depolaması ve koruması gerekir.</span><span class="sxs-lookup"><span data-stu-id="25cda-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="25cda-105">Bir olay anahtarı tarafından dizinlenen bir temsilci koleksiyonunun uygulanması tipik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="25cda-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="25cda-106">Her bir olay için temsilcileri depolamak amacıyla <xref:System.ComponentModel.EventHandlerList> sınıfını kullanabilirsiniz ya da kendi koleksiyonunuzu uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25cda-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="25cda-107">Koleksiyon sınıfı olay anahtarına bağlı olarak ayarlama, erişme ve olay işleyici temsilcisini almak için yöntemler sağlamak zorundadır.</span><span class="sxs-lookup"><span data-stu-id="25cda-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="25cda-108">Örneğin, bir <xref:System.Collections.Hashtable> sınıfı kullanabilir veya <xref:System.Collections.DictionaryBase> sınıfından özel bir sınıf türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25cda-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="25cda-109">Temsilci koleksiyonuna ait uygulama detaylarının sınıfınızın dışında sunulmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="25cda-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="25cda-110">Sınıf içindeki her bir olay özelliği, bir ekleme erişimci yöntemi ve bir kaldırma erişimci yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25cda-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="25cda-111">Bir olay özelliğine ait ekleme erişimcisi girdi temsilci örneğini temsilci koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="25cda-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="25cda-112">Bir olay özelliğine ait kaldırma erişimcisi girdi temsilci örneğini temsilci koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="25cda-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="25cda-113">Olay özellik erişimcileri, örnekleri temsilci koleksiyona eklemek veya kaldırmak için olay özelliği için önceden tanımlanmış anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="25cda-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="25cda-114">Olay özelliklerini kullanarak birden çok olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="25cda-114">To handle multiple events using event properties</span></span>  
  
1.  <span data-ttu-id="25cda-115">Olayları oluşturan sınıf içinde bir temsilci koleksiyon tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="25cda-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2.  <span data-ttu-id="25cda-116">Her bir olay için bir anahtar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="25cda-116">Define a key for each event.</span></span>  
  
3.  <span data-ttu-id="25cda-117">Olayları oluşturan sınıftaki olay özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="25cda-117">Define the event properties in the class that raises the events.</span></span>  
  
4.  <span data-ttu-id="25cda-118">Olay özelliklerine ait ekleme ve kaldırma erişimci yöntemlerini uygulamak için temsilci koleksiyonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="25cda-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5.  <span data-ttu-id="25cda-119">Olayları işleyen sınıflardaki olay işleyici temsilcilerini eklemek ve kaldırmak için ortak olay özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="25cda-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25cda-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="25cda-120">Example</span></span>  
 <span data-ttu-id="25cda-121">Aşağıdaki C# örneği her bir olay temsilcisini depolamak için bir `MouseDown` kullanarak `MouseUp` ve <xref:System.ComponentModel.EventHandlerList> olay özelliklerini uygular.</span><span class="sxs-lookup"><span data-stu-id="25cda-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="25cda-122">Olay özellik yapılarının anahtar kelimeleri kalın yazı tipindedir.</span><span class="sxs-lookup"><span data-stu-id="25cda-122">The keywords of the event property constructs are in bold type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25cda-123">Olay özellikleri [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]'de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="25cda-123">Event properties are not supported in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="25cda-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25cda-124">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
- [<span data-ttu-id="25cda-125">Olaylar</span><span class="sxs-lookup"><span data-stu-id="25cda-125">Events</span></span>](../../../docs/standard/events/index.md)  
- <xref:System.Web.UI.Control.Events%2A>  
- [<span data-ttu-id="25cda-126">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="25cda-126">How to: Declare Custom Events To Conserve Memory</span></span>](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
