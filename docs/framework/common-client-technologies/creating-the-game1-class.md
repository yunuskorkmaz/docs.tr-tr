---
title: "Game1 Sınıfı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 1e4fd15013f10667b397e010fff56b7bc6a0f641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-game1-class"></a>Game1 Sınıfı Oluşturma
Game1 sınıfı türetilen tüm Microsoft XNA projelerle gibi [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) temel grafik cihaz başlatma, oyun mantığı ve kod oyunlar için XNA işleme sağlayan sınıf. Game1 sınıfı işlerin çoğunu içinde GamePiece ve GamePieceCollection sınıfları için oldukça basittir.  
  
## <a name="creating-the-code"></a>Kod oluşturma  
 Sınıfı için özel üyelerin oluşur bir **GamePieceCollection** oyun parçaları tutacak nesne bir [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) nesnesi ve [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) kullanılan nesnesi Oyun parça işlenecek.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Oyun başlatılması sırasında bu nesneler oluşturulur.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Zaman [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) yöntemi çağrıldığında, oyun parçaları oluşturulur ve atanan **GamePieceCollection** nesnesi. Oyun parça iki tür vardır. Parçaları ölçek çarpanını biraz vardır, bazı küçük ve bazı büyük parçalarını şekilde değiştirilir.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Güncelleştirme](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntemi çağrıldığında art arda XNA Framework tarafından oyun çalışırken. [Güncelleştirme](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntem çağrılarını **ProcessInertia** ve **UpdateFromMouse** oyun yöntemlere parçası koleksiyonu. Bu yöntemler açıklanmıştır [GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Çizin](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi olarak da adlandırılır art arda XNA Framework tarafından oyun çalışırken. [Çizin](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi çağrılarak oyun parça işlemeyi gerçekleştirir **çizin** yöntemi **GamePieceCollection** nesnesi. Bu yöntem açıklanan[GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA uygulamasında düzenlemeleri ve Eylemsizliği kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePiece sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Tam kod listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)
