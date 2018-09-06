---
title: XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871050"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="fa2d4-102">XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="fa2d4-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="fa2d4-103">Bu makalede, oyun parçaları hareketini denetlemek için düzenlemeleri ve Eylemsizliği Microsoft XNA uygulamasında işleme nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="fa2d4-104">Bu makalede okumadan önce sahibi olmalısınız [düzenlemelere ve Eylemsizliğe genel bakış](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) konu ve temel XNA ile programlama kavramları hakkında bilgi sahibi olun.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="fa2d4-105">Bu makalede açıklanan görevler gerçekleştirmek için XNA projenizi başvurmalıdır <xref:System.Windows.Input.Manipulations> derlemede olmalıdır [XNA oyun stüdyosu](https://msdn.microsoft.com/library/bb200104.aspx) ([indirme](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) bilgisayarınızda yüklü şekilde, Proje XNA derlemelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([download](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="fa2d4-106">İşlevselliğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="fa2d4-106">Overview of Functionality</span></span>  
 <span data-ttu-id="fa2d4-107">Bu makalede düzenleme ve eylemsizliğe işleme kullanan bir oyun temsil eden özel bir sınıfın nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="fa2d4-108">Bu sınıf fare ile sürükleyerek ve sonra bırakarak oyun bir ekranda yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="fa2d4-109">Yayımlanan sonra tutar işleme için Eylemsizliği olarak kademeli olarak taşıma oyun parça yavaşlar.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="fa2d4-110">Taşıma doğrusal ve angular ' dir.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="fa2d4-111">![Basit düzenlemeler ve eylemsizlik uygulama. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="fa2d4-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="fa2d4-112">Ayrıca, özel bir koleksiyona birden fazla oyun parçaları yöneten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="fa2d4-113">Bu XNA oyununun sınıfından gerekli işleme kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="fa2d4-114">GamePiece Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa2d4-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="fa2d4-115">GamePieceCollection Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa2d4-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="fa2d4-116">Game1 Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa2d4-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="fa2d4-117">Tam Kod Listeleri</span><span class="sxs-lookup"><span data-stu-id="fa2d4-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa2d4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa2d4-118">See Also</span></span>  
 <xref:System.Windows.Input.Manipulations>  
 [<span data-ttu-id="fa2d4-119">Düzenlemelere ve Eylemsizliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa2d4-119">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
