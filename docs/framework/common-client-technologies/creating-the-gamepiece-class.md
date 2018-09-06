---
title: GamePiece Sınıfı Oluşturma
ms.date: 03/30/2017
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
ms.openlocfilehash: eb73918cc03e2621d39a98158d40a839dbc69d80
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857907"
---
# <a name="creating-the-gamepiece-class"></a>GamePiece Sınıfı Oluşturma
**GamePiece** sınıfı Microsoft XNA oyun parça resim yüklenemiyor, oyun parça ile ilgili olarak fare durumunu izleyin, fare yakalama, işleme ve eylemsizliğe işleme sağlamak için gerekli tüm işlevi kapsülleyen ve Oyun parça görünüm sınırlarına ulaştığında Sıçrama yeteneği sağlar.  
  
## <a name="private-members"></a>Özel üyeler  
 Üst kısmındaki **GamePiece** sınıfı, birkaç özel üyeler bildirilir.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Ortak Özellikler  
 Bu özel üyeler üç genel özellikleri aracılığıyla sunulur. **Ölçek** ve **PieceColor** özellikleri ölçek ve parça rengini sırasıyla belirtmek uygulamayı etkinleştirin. **Sınırları** kendisi, ne zaman bir parça başka Kaplama gibi işlemek için başka bir sınır kullanılacak bir parça etkinleştirmek için özellik sunulmuştur. Aşağıdaki kod, ortak özellikler bildirimi gösterir.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Sınıf oluşturucusu  
 Oluşturucusu **GamePiece** sınıfı aşağıdaki parametreleri kabul eder:  
  
-   A [SpriteBatch](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) türü. Burada geçirilen başvuru için özel üye atanır `spriteBatch`ve kullanılan erişimi [SpriteBatch.Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) oyun parça kendisini işler yöntemi. Ayrıca, [GraphicsDevice](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) özelliği oluşturmak için kullanılan [doku](https://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) oyun parça ile ve oyun parça karşılaştığında saptamak amacıyla görünüm boyutunu almak için ilişkili nesne bir Pencere sınır böylece parça Sıçrama.  
  
-   Oyun parçası için kullanılacak bir görüntü dosyası adını belirten dize.  
  
 Oluşturucu ayrıca oluşturur bir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesnesi ve bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> nesne ve olayları için olay işleyicileri oluşturur.  
  
 Aşağıdaki kod Oluşturucusu gösterir **GamePiece** sınıfı.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Fare girişi yakalama  
 **UpdateFromMouse** yöntemdir fare oyun parçanın sınırlar içinde ve algılamak için fare düğmesini serbest bir fare düğmesine basıldığında algılamayla sorumlu.  
  
 (Fare parça sınırları içinde olan) farenin sol düğmesine basıldığında, bu yöntem bu oyun parça fare yakalandı ve işleme işleme başlar belirten bir bayrak ayarlar.  
  
 Düzenleme işlemi, bir dizi oluşturarak başlatıldığında <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri ve bunlara geçirerek <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesne. Bu, manipülatörleri (Bu durumda bir tek işleyici) olarak değerlendirin ve işleme olay işleme işlemci neden olur.  
  
 Ayrıca, hangi sürükleme oluştuğunu noktası kaydedilir. Bu, daha sonra sırasında kullanılır <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> delta çeviri ayarlamak için olay değerlerinden Sürükle noktanın arkasında satırına oyun parça swings.  
  
 Son olarak, bu yöntem, fare yakalama durumunu döndürür. Böylece [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) oyun birden çok parça olduğunda yakalama yönetmek için nesne.  
  
 Aşağıdaki kodda gösterildiği **UpdateFromMouse** yöntemi.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>İşlemeleri işleme  
 İşleme başladığında <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> olayı oluşturulur. Bu olay işleyicisi oluştuğunu ve ayarlar Eylemsizliği işlemeyi durdurur *processInertia* bayrak `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 İşleme değişiklikle ilişkili değerler olarak <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olayı oluşturulur. Bu olay işleyicisi, oyun parça konum ve dönüş değerlerinin değişiklik yapmak için olay bağımsız değişkenleri geçirildi değişim değerleri kullanır.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Bir işleme ile ilişkili olan manipülatörleri (Bu durumda, bir tek işleyici içinde) tüm kaldırıldığında, işleme işlemci başlatır <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olay. Bu olay işleyicisi bu olay bağımsız değişkenleri tarafından bildirilen için Eylemsizliği işlemcisi ilk hızlarda ayarlayarak işleme için Eylemsizliği başlar ve ayarlar *processInertia* bayrak `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Eylemsizlik işleme  
 Yeni değerler döndürme, angular ve doğrusal hızlarda ve konumu (çeviri) koordinatları için Eylemsizliği işleme extrapolates gibi <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olayı oluşturulur. Bu olay işleyicisi, oyun parçanın döndürme ve konumunu değiştirmek için olay bağımsız değişkenleri geçirildi değişim değerleri kullanır.  
  
 Görünüm bağlantı noktası sınırları dışında hareket oyun parçadaki yeni koordinatları yol açarsa Eylemsizliği işleme hızı ters çevrilir. Bu oyun parça, karşılaştı görünümü bağlantı noktası sınır gelmesine neden olur.  
  
 Özelliklerini değiştiremezsiniz bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> görevlendirebilir çalışırken nesne. Bu nedenle, X veya Y hız ters, olay işleyicisi ilk Eylemsizliği çağırarak sona erer <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> yöntemi. Ardından geçerli hız değerlerin (sponge davranışı için ayarlanmış) olmasını yeni başlangıç hızı değerleri atar ve ayarlar *processInertia* bayrak `true`.  
  
 Aşağıdaki kod için olay işleyicisini gösterir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olay.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Eylemsizlik işleme tamamlandıktan sonra için Eylemsizliği işlemcisi başlatır <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> olay. Bu olay işleyicisi ayarlar *processInertia* bayrak `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Şu ana kadar sunulan mantıksal hiçbiri gerçekten gerçekleşmesi Eylemsizliği görevlendirebilir neden olur. Bu, gerçekleştirilir **ProcessInertia** yöntemi. Bu yöntem, oyun güncelleştirme döngüden art arda çağrılır ( [Game.Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntemi) denetler *processInertia* bayrağı ayarlandığında `true`ve bu durumda, çağıran <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> yöntem. Bu oluşmasına neden görevlendirebilir yöntemi ve harekete geçirirse çağırma <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olay.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Draw yöntemi aşırı yüklemelerinden çağrılana kadar oyun parça gerçekten işlenmez. Bu yöntemin ilk aşırı yükleme oyun çizim döngüden art arda çağrılır ( [Game.Draw](https://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi). Bu, geçerli konumu, döndürme ve ölçeklendirme Etkenler oyun parçasını işler.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Ek Özellikler  
 Üç özel özellikleri tarafından kullanılan **GamePiece** sınıfı.  
  
1.  **Zaman damgası** – işleme düzenlemeleri ve Eylemsizliği işlemcileri tarafından kullanılacak bir zaman damgası değeri alır.  
  
2.  **X** – alır veya ayarlar oyun parçanın X koordinatı. İsabet sınaması ve işleme işlemci pivot konumu için kullanılan sınırları ayarlarken, ayarlar.  
  
3.  **Y** – alır veya ayarlar oyun parçanın Y koordinatı. İsabet sınaması ve işleme işlemci pivot konumu için kullanılan sınırları ayarlarken, ayarlar.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve Eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA Uygulamasında Düzenlemeleri ve Eylemsizliği Kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePieceCollection Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Game1 Sınıfı Oluşturma](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
