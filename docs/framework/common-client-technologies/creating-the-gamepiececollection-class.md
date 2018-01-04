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
ms.workload: dotnet
ms.openlocfilehash: 8f000c1eed27acc16d158cb893cba876ea016277
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-gamepiececollection-class"></a>GamePieceCollection Sınıfı Oluşturma
**GamePieceCollection** sınıfı genel listesi sınıfından türetilen ve birden çok daha kolay yönetmek için yöntemler sunar **GamePiece** nesneleri.  
  
## <a name="creating-the-code"></a>Kod oluşturma  
 Oluşturucusunun **GamePieceCollection** sınıfı başlatır özel üye *capturedIndex*. Bu alan izlemek için olan oyun parçaları şu anda fare yakalama kullanılır.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** ve **çizin** yöntemleri basitleştirmek oyunda gereken kod [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) ve [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemler tarafından koleksiyondaki oyun şey numaralandırma ve her birini ilgili yöntemi çağırma **GamePiece** nesnesi.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** yöntemi, oyun güncelleştirme sırasında da çağrılır. Fareyi ilk (varsa) geçerli yakalama hala etkin olup olmadığını kontrol ederek yakalamak yalnızca bir oyun parça sağlar. Bu durumda, diğer bir parça yakalamaya denetleyin izin verilmez.  
  
 Hiçbir parça şu anda yakalama varsa **UpdateFromMouse** yöntemi her oyun taş sonuncudan ilk numaralandırır ve yakalama parçasının fare raporları durumunda olup olmadığını kontrol eder. Öyleyse, parçasının geçerli yakalanan parçası haline gelir ve başka bir işleme gerçekleşir. **UpdateFromMouse** böylece iki parça çakışan, daha yüksek Z düzeni ile bir yakalama elde yöntemi koleksiyondaki son öğenin ilk denetler. Z düzeni açık olmadığı değiştirilebilir değil; yalnızca oyun taşları koleksiyonuna eklenen sıraya göre tabidir.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve Eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePiece Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Game1 Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Tam Kod Listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)
