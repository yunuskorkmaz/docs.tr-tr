---
title: "GamePiece Sınıfı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: "9"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 989883034b30c3ec67f5441c5512418643546519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-the-gamepiece-class"></a>GamePiece Sınıfı Oluşturma
**GamePiece** sınıfı yalıtır Microsoft XNA oyun parça görüntü yükleme, oyun parça sitedeki fare durumunu izlemek, fare yakalama, düzenleme ve eylemsizlik işleme sağlamak için gerekli tüm işlevlere ve Oyun parça görünümü bağlantı noktasının sınırlarını ulaştığında Sıçrama yeteneği sağlar.  
  
## <a name="private-members"></a>Özel üyeler  
 Üstündeki **GamePiece** sınıfı, birkaç özel üyelerin bildirildiğinde.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Ortak Özellikler  
 Bu özel üyelerin üç ortak özellikler sunulur. **Ölçek** ve **PieceColor** özellikleri etkinleştirin uygulamanın sırasıyla ölçeği ve parça rengini belirtir. **Sınırları** özelliği başka bir sınır kendisi, ne zaman bir parça başka Kaplama gibi işlemek için kullanılacak bir parça etkinleştirmek için gösterilir. Aşağıdaki kod genel özelliklerin bildirimi gösterir.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Sınıf oluşturucusu  
 Oluşturucusu **GamePiece** sınıfı aşağıdaki parametreleri kabul eder:  
  
-   A [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) türü. Özel üye burada geçirilen başvuru atanan `spriteBatch`ve kullanılan erişimi [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) oyun parça kendisini işler yöntemi. Ayrıca, [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) özelliği oluşturmak için kullanılan [doku](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) oyun parçası olan ve oyun parça karşılaştığında saptamak amacıyla görünüm bağlantı noktası boyutunu edinmek için ilişkili nesne bir Pencere sınır böylece parça Sıçrama.  
  
-   Oyun parça için kullanılacak görüntünün dosya adını belirten dize.  
  
 Ayrıca Oluşturucusu oluşturur bir <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesne ve bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> nesne ve bunların olayları için olay işleyicileri oluşturur.  
  
 Aşağıdaki kod Oluşturucusu gösterir **GamePiece** sınıfı.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Fare girişi yakalama  
 **UpdateFromMouse** yöntemdir fare oyun parça sınırlar içinde ve ne zaman algılamak için fare düğmesini yayımlandı fare düğmesine basıldığında algılamayla sorumlu.  
  
 (Fare parça sınırları içinde iken) sol fare düğmesine basıldığında, bu yöntem bu oyun parça fare yakalandı ve denetleme işleme başlar belirten bir bayrak ayarlar.  
  
 Denetleme işleme, bir dizi oluşturarak başlatıldığında <xref:System.Windows.Input.Manipulations.Manipulator2D> nesneleri ve bunlara geçirme <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> nesnesi. Bu, manipülatörleri (Bu durumda bir tek manipulator) olarak değerlendirmek ve işleme olaylarını işleme işlemci neden olur.  
  
 Ayrıca, sürükle gerçekleştiğini noktası kaydedilir. Bu, daha sonra sırasında kullanılır <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> delta çeviri ayarlamak için olay noktayı sürükleyin arkasında hale oyun parça swings böylece değerleri.  
  
 Son olarak, bu yöntem, fare yakalama durumunu döndürür. Böylece [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) birden çok oyun parça olduğunda yakalama yönetmek için nesnesi.  
  
 Aşağıdaki kodda gösterildiği **UpdateFromMouse** yöntemi.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>İşlemeleri işleme  
 Düzenleme işlemi başladığında, <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> olayı oluşturulur. Bu olay işleyicisi oluştuğunu ve ayarlar eylemsizlik işlemeyi durdurur *processInertia* bayrağını `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 İşleme değişiklikle ilişkili değerler olarak <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> olayı oluşturulur. Bu olay işleyicisi oyun parça konum ve dönüş değerleri için değişiklik yapmak için olay bağımsız değişken geçirildi delta değerleri kullanır.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Tüm işleme ile ilişkili manipülatörleri (Bu durumda, bir tek manipulator içinde) kaldırıldığında, işleme işlemci başlatır <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> olay. Bu olay işleyicisi bu olay bağımsız değişkenleri tarafından bildirilen üzere eylemsizlik işlemcinin ilk velocities ayarlayarak işlemleri eylemsizlik başlar ve ayarlar *processInertia* bayrağını `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Eylemsizlik işleme  
 Eylemsizlik işleme Açısal ve doğrusal velocities, konumu (çevirisi) koordinatları ve döndürme, yeni değerleri extrapolates gibi <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olayı oluşturulur. Bu olay işleyicisi, konum ve oyun parça dönüşünü değiştirmek için olay bağımsız değişken geçirildi delta değerleri kullanır.  
  
 Görünüm bağlantı noktası sınırlarının dışına taşıma oyun parçadaki yeni koordinatlar neden oluyorsa eylemsizlik işleme hızı ters çevrilir. Bu, oyun parça, karşılaştı görünüm bağlantı noktası sınır gelmesine neden olur.  
  
 Özelliklerini değiştiremezsiniz bir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> dış değer bulmayı çalışırken nesne. Bu nedenle, X veya Y hız Ters kaydederken, olay işleyicisi ilk eylemsizlik çağırarak durdurur <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> yöntemi. Ardından (Sünger davranışını ayarlanır) geçerli hız değerler yeni ilk hız değerleri atar ve ayarlar *processInertia* bayrağını `true`.  
  
 Aşağıdaki kod için olay işleyicisini gösterir <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olay.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Eylemsizlik işlem tamamlandığında, eylemsizlik işlemci başlatır <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> olay. Bu olay işleyicisi ayarlar *processInertia* bayrağını `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Şu ana kadar sunulan mantığı hiçbiri gerçekte gerçekleşmek üzere eylemsizlik dış değer bulmayı neden olur. Bu, gerçekleştirilir **ProcessInertia** yöntemi. Bu yöntem oyun güncelleştirme döngüden sürekli olarak adlandırılır ( [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) yöntemi) denetler *processInertia* bayrağı ayarlanmış `true`ve bu durumda, çağıran <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> yöntem. Bu yöntem nedenler görevlendirebilir gerçekleşmesi için ve başlatır çağırma <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> olay.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Draw yöntemi aşırı yüklemelerinden birini çağrılıncaya kadar oyun parça gerçekte işlenmez. Bu yöntem ilk yüklemesini tekrar tekrar oyun çizim döngüden adlı ( [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) yöntemi). Geçerli konumu, döndürme ve ölçek Etkenler oyun parça işler.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Ek Özellikler  
 Üç özel özellikleri tarafından kullanılan **GamePiece** sınıfı.  
  
1.  **Zaman damgası** – işleme ve eylemsizlik işlemcileri tarafından kullanılmak üzere bir zaman damgası değeri alır.  
  
2.  **X** – alır veya ayarlar oyun parça X koordinatı. İsabet testi ve işleme işlemci Özet konumu için kullanılan sınırları ayarlarken, ayarlar.  
  
3.  **Y** – alır veya ayarlar oyun parça Y koordinatı. İsabet testi ve işleme işlemci Özet konumu için kullanılan sınırları ayarlarken, ayarlar.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenlemeler ve eylemsizlik](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [XNA uygulamasında düzenlemeleri ve Eylemsizliği kullanma](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [GamePieceCollection sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Game1 sınıfı oluşturma](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
