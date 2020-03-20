---
title: İç İçe Grafik Kapsayıcılarını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182472"
---
# <a name="using-nested-graphics-containers"></a>İç İçe Grafik Kapsayıcılarını Kullanma
GDI+, bir <xref:System.Drawing.Graphics> nesnedeki durum bölümünü geçici olarak değiştirmek veya artırmak için kullanabileceğiniz kapsayıcılar sağlar. Bir nesnenin yöntemini <xref:System.Drawing.Graphics.BeginContainer%2A> çağırarak <xref:System.Drawing.Graphics> bir kapsayıcı oluşturursunuz. İç içe <xref:System.Drawing.Graphics.BeginContainer%2A> kapsayıcılar oluşturmak için art arda arayabilirsiniz. Her <xref:System.Drawing.Graphics.BeginContainer%2A> çağrı için bir çağrı ile <xref:System.Drawing.Graphics.EndContainer%2A>eşleştirilmiş olmalıdır.  
  
## <a name="transformations-in-nested-containers"></a>İç Içe Kapsayıcılarda Dönüşümler  
 Aşağıdaki örnek, bu <xref:System.Drawing.Graphics> <xref:System.Drawing.Graphics> nesnenin içinde bir nesne ve kapsayıcı oluşturur. Nesnenin <xref:System.Drawing.Graphics> dünya dönüşümü x yönünde 100 birim, y yönünde ise 80 birim lik bir çeviridir. Konteynerin dünya dönüşümü 30 derecelik bir dönüş. Kod aramayı `DrawRectangle(pen, -60, -30, 120, 60)` iki kez yapar. İlk çağrı <xref:System.Drawing.Graphics.DrawRectangle%2A> konteynerin içindedir; diğer bir deyişle, arama aramaları <xref:System.Drawing.Graphics.BeginContainer%2A> arasında <xref:System.Drawing.Graphics.EndContainer%2A>ve . İkinci çağrı. <xref:System.Drawing.Graphics.DrawRectangle%2A> <xref:System.Drawing.Graphics.EndContainer%2A>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Önceki kodda, kapsayıcının içinden çizilen dikdörtgen önce kapsayıcının dünya dönüşümü (döndürme) ve daha sonra <xref:System.Drawing.Graphics> nesnenin dünya dönüşümü (çeviri) tarafından dönüştürülür. Kapsayıcının dışından çizilen dikdörtgen, yalnızca <xref:System.Drawing.Graphics> nesnenin dünya dönüşümü (çeviri) ile dönüştürülür. Aşağıdaki resimde iki dikdörtgen gösterilmektedir:
  
 ![İç içe kapsayıcıları gösteren çizim.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>İç Içe Kapsayıcılarda Kırpma  
 Aşağıdaki örnek, iç içe kapların kırpma bölgelerini nasıl işleyeceğini göstermektedir. Kod, bu <xref:System.Drawing.Graphics> <xref:System.Drawing.Graphics> nesnenin içinde bir nesne ve kapsayıcı oluşturur. Nesnenin <xref:System.Drawing.Graphics> kırpma bölgesi bir dikdörtgen, kapsayıcının kırpma bölgesi ise bir elipstir. Kod <xref:System.Drawing.Graphics.DrawLine%2A> yönteme iki arama yapar. İlk arama <xref:System.Drawing.Graphics.DrawLine%2A> kapsayıcının içinde, ikinci arama <xref:System.Drawing.Graphics.DrawLine%2A> ise kapsayıcının dışındadır (çağrıdan <xref:System.Drawing.Graphics.EndContainer%2A>sonra). İlk satır, iki kırpma bölgesinin kesiştiği noktada kırpılır. İkinci satır yalnızca <xref:System.Drawing.Graphics> nesnenin dikdörtgen kırpma bölgesi tarafından kırpılır.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Aşağıdaki resimde kırpılan iki satır gösterilmektedir:
  
 ![Kırpılmış çizgileri olan iç içe bir kapsayıcıyı gösteren çizim.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Önceki iki örnekte de belirtildiği gibi, dönüşümler ve kırpma bölgeleri iç içe kaplarda birikmelidir. Kapsayıcının ve <xref:System.Drawing.Graphics> nesnenin dünya dönüşümlerini ayarlarsanız, her iki dönüşüm de kapsayıcının içinden çekilen öğeler için de geçerli olur. Önce kapsayıcının dönüşümü, <xref:System.Drawing.Graphics> nesnenin dönüşümü ise ikinci olarak uygulanacaktır. Kapsayıcının ve <xref:System.Drawing.Graphics> nesnenin kırpma bölgelerini ayarlarsanız, kapsayıcının içinden çizilen öğeler iki kırpma bölgesinin kesiştiği nokta tarafından kırpılır.  
  
## <a name="quality-settings-in-nested-containers"></a>İç Içe Kapsayıcılarda Kalite Ayarları  
 İç içe<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>kaplarda kalite ayarları (, ve benzeri) kümülatif değildir; bunun yerine, kapsayıcının kalite ayarları geçici olarak <xref:System.Drawing.Graphics> bir nesnenin kalite ayarlarını değiştirir. Yeni bir kapsayıcı oluşturduğunuzda, bu kapsayıcının kalite ayarları varsayılan değerlere ayarlanır. Örneğin, düzgünleme moduna sahip bir <xref:System.Drawing.Graphics> nesneniz olduğunu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>varsayalım. Bir kapsayıcı oluşturduğunuzda, kapsayıcının içindeki yumuşatma modu varsayılan yumuşatma modudur. Kapsayıcının yumuşatma modunu ayarlamakta özgürsunuz ve kapsayıcının içinden çekilen öğeler ayarladığınız moda göre çizilir. Aramadan <xref:System.Drawing.Graphics.EndContainer%2A> sonra çizilen öğeler, çağrıdan önce<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>yerinde olan yumuşatma moduna <xref:System.Drawing.Graphics.BeginContainer%2A>( ) göre çizilir.  
  
## <a name="several-layers-of-nested-containers"></a>İç içe kapsayıcıların çeşitli katmanları  
 Bir <xref:System.Drawing.Graphics> nesnedeki bir kapsayıcıyla sınırlı değildir. Her biri bir önceki iç içe olan kapsayıcılar dizisi oluşturabilir ve bu iç içe geçen kapsayıcıların her birinin dünya dönüşümünü, kırpma bölgesini ve kalite ayarlarını belirtebilirsiniz. En içteki kapsayıcının içinden bir çizim yöntemi çağırırsanız, dönüşümler en içteki kapsayıcıdan başlayıp en dıştaki kapsayıcıyla biten sırayla uygulanır. En içteki kapsayıcının içinden çekilen öğeler, tüm kırpma bölgelerinin kesiştiği noktada kırpılır.  
  
 Aşağıdaki örnekbir <xref:System.Drawing.Graphics> nesne oluşturur ve metin oluşturma <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>ipucunu . Kod, biri diğeri içinde iç içe olmak üzere iki kapsayıcı oluşturur. Dış kapsayıcının metin oluşturma ipucu ayarlanır <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>ve iç kapsayıcının metin oluşturma ipucu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod üç dize çizer: biri iç kapsayıcıdan, biri dış <xref:System.Drawing.Graphics> kapsayıcıdan ve diğeri de nesnenin kendisinden.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Aşağıdaki resimde üç dizeleri gösterilmektedir. İç kapsayıcıdan ve <xref:System.Drawing.Graphics> nesneden çekilen dizeleri antialiasing tarafından düzeltilir. <xref:System.Drawing.Graphics.TextRenderingHint%2A> Dış kapsayıcıdan çizilen dize, özelliği <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![İç içe kaplardan çekilen dizeleri gösteren çizim.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- [Bir Grafik Nesnesinin Durumunu Yönetme](managing-the-state-of-a-graphics-object.md)
