---
title: Game1 Sınıfı Oluşturma
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: 368da9df4dffc7017abb02888bc2eb2641f04b8b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201029"
---
# <a name="creating-the-game1-class"></a>Game1 Sınıfı Oluşturma
Tüm Microsoft XNA projeler Game1 sınıfı türetilen gibi [Microsoft.Xna.Framework.Game](https://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) temel grafik cihazı başlatma, oyun mantığı ve kod için XNA oyunlar oluşturma sağlar sınıfını. Game1 sınıfı çoğunu içinde GamePiece ve GamePieceCollection sınıfları için oldukça basittir.  
  
## <a name="creating-the-code"></a>Kod oluşturma  
 Özel üyeleri sınıfın oluşur bir **GamePieceCollection** oyun parçaları tutacak nesne bir [GraphicsDeviceManager](https://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) nesnesi ve bir [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) kullanılan nesnesi Oyun parçaları işlemek için.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Oyun başlatma sırasında bu nesneler örneği oluşturulur.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Zaman [LoadContent](https://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) yöntemi çağrıldığında, oyun parçaları oluşturuldu ve atandı **GamePieceCollection** nesne. Oyun parçaları iki tür vardır. Bazı küçük ve bazı büyük parçalarını olduğundan parçaları ölçek çarpanını biraz değişti.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Güncelleştirme](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntemi çağrıldığında tekrar tekrar XNA Framework tarafından oyun çalışırken. [Güncelleştirme](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntem çağrılarını **ProcessInertia** ve **UpdateFromMouse** oyun yöntemlerde parçası koleksiyonu. Bu yöntemler açıklanmıştır [GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Çizmek](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi de çağrılır art arda XNA Framework tarafından oyun çalışırken. [Çizmek](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi çağırarak oyun parçaları işlenmesini gerçekleştirir **çizmek** yöntemi **GamePieceCollection** nesne. Bu yöntem açıklanan[GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve Eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePiece Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [GamePieceCollection Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Tam Kod Listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)
