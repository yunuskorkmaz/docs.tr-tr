---
title: "GamePieceCollection Sınıfı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: b8b53e5890aaebbad2f0a5f0e058182193b11622
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="29f58-102">GamePieceCollection Sınıfı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f58-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="29f58-103">**GamePieceCollection** sınıfı genel listesi sınıfından türetilen ve birden çok daha kolay yönetmek için yöntemler sunar **GamePiece** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="29f58-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="29f58-104">Kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f58-104">Creating the Code</span></span>  
 <span data-ttu-id="29f58-105">Oluşturucusunun **GamePieceCollection** sınıfı başlatır özel üye *capturedIndex*.</span><span class="sxs-lookup"><span data-stu-id="29f58-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="29f58-106">Bu alan izlemek için olan oyun parçaları şu anda fare yakalama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29f58-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 <span data-ttu-id="29f58-107">**ProcessInertia** ve **çizin** yöntemleri basitleştirmek oyunda gereken kod [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) ve [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemler tarafından koleksiyondaki oyun şey numaralandırma ve her birini ilgili yöntemi çağırma **GamePiece** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="29f58-107">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 <span data-ttu-id="29f58-108">**UpdateFromMouse** yöntemi, oyun güncelleştirme sırasında da çağrılır.</span><span class="sxs-lookup"><span data-stu-id="29f58-108">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="29f58-109">Fareyi ilk (varsa) geçerli yakalama hala etkin olup olmadığını kontrol ederek yakalamak yalnızca bir oyun parça sağlar.</span><span class="sxs-lookup"><span data-stu-id="29f58-109">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="29f58-110">Bu durumda, diğer bir parça yakalamaya denetleyin izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="29f58-110">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="29f58-111">Hiçbir parça şu anda yakalama varsa **UpdateFromMouse** yöntemi her oyun taş sonuncudan ilk numaralandırır ve yakalama parçasının fare raporları durumunda olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="29f58-111">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="29f58-112">Öyleyse, parçasının geçerli yakalanan parçası haline gelir ve başka bir işleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="29f58-112">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="29f58-113">**UpdateFromMouse** böylece iki parça çakışan, daha yüksek Z düzeni ile bir yakalama elde yöntemi koleksiyondaki son öğenin ilk denetler.</span><span class="sxs-lookup"><span data-stu-id="29f58-113">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="29f58-114">Z düzeni açık olmadığı değiştirilebilir değil; yalnızca oyun taşları koleksiyonuna eklenen sıraya göre tabidir.</span><span class="sxs-lookup"><span data-stu-id="29f58-114">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a><span data-ttu-id="29f58-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29f58-115">See Also</span></span>  
 [<span data-ttu-id="29f58-116">Düzenlemeler ve eylemsizlik</span><span class="sxs-lookup"><span data-stu-id="29f58-116">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="29f58-117">XNA uygulamasında düzenlemeleri ve Eylemsizliği kullanma</span><span class="sxs-lookup"><span data-stu-id="29f58-117">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="29f58-118">GamePiece sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f58-118">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="29f58-119">Game1 sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="29f58-119">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [<span data-ttu-id="29f58-120">Tam kod listeleri</span><span class="sxs-lookup"><span data-stu-id="29f58-120">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
