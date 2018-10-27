---
title: Game1 Sınıfı Oluşturma
ms.date: 03/30/2017
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
ms.openlocfilehash: c96fa846d11947af03faec26dd6de99e0aeec052
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452803"
---
# <a name="creating-the-game1-class"></a>Game1 Sınıfı Oluşturma
Tüm Microsoft XNA projeler Game1 sınıfı türetilen gibi [Microsoft.Xna.Framework.Game](https://docs.microsoft.com/previous-versions/windows/xna/bb197040%28v%3dxnagamestudio.41%29) temel grafik cihazı başlatma, oyun mantığı ve kod için XNA oyunlar oluşturma sağlar sınıfını. Game1 sınıfı çoğunu içinde GamePiece ve GamePieceCollection sınıfları için oldukça basittir.  
  
## <a name="creating-the-code"></a>Kod oluşturma  
 Özel üyeleri sınıfın oluşur bir **GamePieceCollection** oyun parçaları tutacak nesne bir [GraphicsDeviceManager](https://docs.microsoft.com/previous-versions/windows/xna/bb197317%28v%3dxnagamestudio.41%29) nesnesi ve bir [SpriteBatch](https://docs.microsoft.com/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) kullanılan nesnesi Oyun parçaları işlemek için.  
  
 [!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]  
  
 Oyun başlatma sırasında bu nesneler örneği oluşturulur.  
  
 [!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]  
  
 Zaman [LoadContent](https://docs.microsoft.com/previous-versions/windows/xna/bb975766%28v%3dxnagamestudio.41%29) yöntemi çağrıldığında, oyun parçaları oluşturuldu ve atandı **GamePieceCollection** nesne. Oyun parçaları iki tür vardır. Bazı küçük ve bazı büyük parçalarını olduğundan parçaları ölçek çarpanını biraz değişti.  
  
 [!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]  
  
 [Güncelleştirme](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) yöntemi çağrıldığında tekrar tekrar XNA Framework tarafından oyun çalışırken. [Güncelleştirme](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) yöntem çağrılarını **ProcessInertia** ve **UpdateFromMouse** oyun yöntemlerde parçası koleksiyonu. Bu yöntemler açıklanmıştır [GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]  
  
 [Çizmek](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) yöntemi de çağrılır art arda XNA Framework tarafından oyun çalışırken. [Çizmek](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) yöntemi çağırarak oyun parçaları işlenmesini gerçekleştirir **çizmek** yöntemi **GamePieceCollection** nesne. Bu yöntem açıklanan[GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).  
  
 [!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve Eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePiece Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [GamePieceCollection Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Tam Kod Listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)
