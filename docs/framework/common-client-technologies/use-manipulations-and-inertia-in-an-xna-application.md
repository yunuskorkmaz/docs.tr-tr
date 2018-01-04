---
title: "XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7452a6001742bc9e0456ccb6339f13596a2ab72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="73e3f-102">XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="73e3f-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="73e3f-103">Bu makalede, oyun parça hareketini denetlemek için düzenlemeler ve eylemsizlik Microsoft XNA uygulamasında işleme nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="73e3f-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="73e3f-104">Bu makalede okumadan önce aşina olmalısınız [düzenlemelere ve Eylemsizliğe genel bakış](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) konusuna ve temel XNA ile programlama kavramları hakkında bilgi sahibi olun.</span><span class="sxs-lookup"><span data-stu-id="73e3f-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="73e3f-105">Bu makalede açıklanan görevleri gerçekleştirmek için XNA projenizi başvurmalıdır <xref:System.Windows.Input.Manipulations> derleme ve olmalıdır [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([karşıdan](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)), bu nedenle, bilgisayarınızda, Proje XNA derlemeleri başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="73e3f-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="73e3f-106">İşlevselliğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="73e3f-106">Overview of Functionality</span></span>  
 <span data-ttu-id="73e3f-107">Bu makalede işleme ve eylemsizlik işleme kullanan bir oyun gösteren özel bir sınıfın nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73e3f-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="73e3f-108">Bu sınıf, bir oyun parça fareyle sürükleyin ve bunu serbest ekran boyunca yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="73e3f-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="73e3f-109">Serbest sonra tutar işleme eylemsizlik kademeli taşımadan oyun parça yavaşlar.</span><span class="sxs-lookup"><span data-stu-id="73e3f-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="73e3f-110">Doğrusal ve Açısal taşıma.</span><span class="sxs-lookup"><span data-stu-id="73e3f-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="73e3f-111">![Basit düzenlemeler ve eylemsizlik uygulama. ] (../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="73e3f-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="73e3f-112">Ayrıca, özel bir koleksiyona, birden çok oyun parça yöneten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73e3f-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="73e3f-113">XNA oyun sınıfından gereklidir işleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="73e3f-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="73e3f-114">GamePiece Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73e3f-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="73e3f-115">GamePieceCollection Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73e3f-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="73e3f-116">Game1 Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73e3f-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="73e3f-117">Tam Kod Listeleri</span><span class="sxs-lookup"><span data-stu-id="73e3f-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="73e3f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73e3f-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="73e3f-119">Düzenlemelere ve Eylemsizliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="73e3f-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
