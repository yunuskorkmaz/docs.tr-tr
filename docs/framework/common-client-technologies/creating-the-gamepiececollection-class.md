---
title: GamePieceCollection Sınıfı Oluşturma
ms.date: 03/30/2017
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
ms.openlocfilehash: 0a39ca479e9b370b027fcec4bcf76996e6191296
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190586"
---
# <a name="creating-the-gamepiececollection-class"></a>GamePieceCollection Sınıfı Oluşturma
**GamePieceCollection** sınıfı genel bir liste sınıftan türetilen ve çok daha kolay yönetmek için yöntemleri tanıtır **GamePiece** nesneleri.  
  
## <a name="creating-the-code"></a>Kod oluşturma  
 Oluşturucusuna **GamePieceCollection** sınıfı başlatır özel üye *capturedIndex*. Bu alanda izlemek için olan oyun parçaları şu anda fare yakalama kullanılır.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** ve **çizmek** yöntemleri oyunda gerekli kodu basitleştirmek [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) ve [Game.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) yöntemlerle Oyun parçaları koleksiyondaki tüm numaralandırma ve ilgili yöntemini her çağırmak **GamePiece** nesne.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** yöntemi, oyun güncelleştirme sırasında da çağrılır. Ancak, fareyi ilk yakalamanın (varsa) hala etkin olup olmadığını kontrol ederek yakalamak yalnızca bir oyun parça etkinleştirir. Bu durumda, diğer bir parça yakalamaya denetlemek izin verilmez.  
  
 Hiçbir parça şu anda yakalama varsa **UpdateFromMouse** yöntemi sonuncudan oyun her parça için ilk numaralandırır ve yakalama olan İnceleyenleri fare raporları durumunda olup olmadığını kontrol eder. Bu durumda, geçerli yakalanan parçası olan İnceleyenleri olur ve daha fazla işleme gerçekleşir. **UpdateFromMouse** iki parça çakışan, en üst Z düzenini yakalama alacaktır, böylece yöntemi koleksiyondaki son öğenin ilk denetler. Z düzenini, açık ya da takımdaki herhangi biri değil; Sipariş oyun parçaları bir koleksiyona eklenmesini tabidir.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve Eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePiece Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Game1 Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Tam Kod Listeleri](../../../docs/framework/common-client-technologies/full-code-listings.md)
