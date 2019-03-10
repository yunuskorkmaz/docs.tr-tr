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
ms.openlocfilehash: 639b53ada8639ed686d04b4aa2e5295ca08240b0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714183"
---
# <a name="using-nested-graphics-containers"></a>İç İçe Grafik Kapsayıcılarını Kullanma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] geçici olarak değiştirin ya da durumda parçası genişletmek için kullanabileceğiniz kapsayıcılar sağlayarak bir <xref:System.Drawing.Graphics> nesne. Bir kapsayıcı oluşturmanız <xref:System.Drawing.Graphics.BeginContainer%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne. Çağırabilirsiniz <xref:System.Drawing.Graphics.BeginContainer%2A> sürekli olarak iç içe geçmiş kapsayıcılar oluşturmak için. Her çağrı <xref:System.Drawing.Graphics.BeginContainer%2A> bir çağrı ile eşleştirilmelidir <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>İç içe geçmiş kapsayıcılar dönüşümleri  
 Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Graphics> nesnesi ve bir kapsayıcı içindeki <xref:System.Drawing.Graphics> nesne. Dünya dönüşümü <xref:System.Drawing.Graphics> nesnedir x yönünde 100 çeviri biriminde ve y yönünde 80 birimlik. Gerçek koordinat dönüştürmesini kapsayıcının 30 derece döndürme ' dir. Kod çağrıda `DrawRectangle(pen, -60, -30, 120, 60)` iki kez. İlk çağrıda <xref:System.Drawing.Graphics.DrawRectangle%2A> kapsayıcının içinde; diğer bir deyişle, çağrıları arasında çağrıdır <xref:System.Drawing.Graphics.BeginContainer%2A> ve <xref:System.Drawing.Graphics.EndContainer%2A>. İçin yapılan ikinci çağrı <xref:System.Drawing.Graphics.DrawRectangle%2A> çağrısı sonra <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Önceki kodda, gerçek koordinat dönüştürmesini kapsayıcısının (döndürme) ve ardından gerçek koordinat dönüştürmesini göre ilk öğesinden kapsayıcısının içinde çizilmiş dikdörtgen dönüştürülür <xref:System.Drawing.Graphics> nesne (çeviri). Yalnızca gerçek koordinat dönüştürmesini tarafından gelen kapsayıcı dışında çizilmiş dikdörtgen dönüştürülür <xref:System.Drawing.Graphics> nesne (çeviri). Aşağıdaki çizimde, iki dikdörtgenler gösterir.  
  
 ![İç içe geçmiş kapsayıcılar](./media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>İç içe geçmiş kapsayıcılarda kırpma  
 Aşağıdaki örnek nasıl iç içe geçmiş kapsayıcılar gösterir kırpma bölgeleri tanıtıcı. Kod oluşturur bir <xref:System.Drawing.Graphics> nesnesi ve bir kapsayıcı içindeki <xref:System.Drawing.Graphics> nesne. Kırpma bölgesini <xref:System.Drawing.Graphics> nesne bir dikdörtgen ve kırpma bölgesinin kapsayıcının elips. Kod iki çağrılar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi. İlk çağrıda <xref:System.Drawing.Graphics.DrawLine%2A> kapsayıcı ve ikinci çağrının içinde <xref:System.Drawing.Graphics.DrawLine%2A> kapsayıcıdır dışında (çağrısından sonra <xref:System.Drawing.Graphics.EndContainer%2A>). İlk satır, kırpma iki bölgeleri kesişimi ile kırpılır. İkinci satır yalnızca dikdörtgen kırpma bölgesini tarafından kırpılır <xref:System.Drawing.Graphics> nesne.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Aşağıdaki çizimde, iki kırpılmış satır gösterir.  
  
 ![İç içe kapsayıcı](./media/nestedcontainers2.png "nestedcontainers2")  
  
 İki Yukarıdaki örneklerde gösterildiği gibi dönüşümler ve kırpma bölgeleri içinde iç içe geçmiş kapsayıcılar bunların toplamı olur. Kapsayıcının dünya dönüştürmeleri ayarlarsanız ve <xref:System.Drawing.Graphics> nesnesi, her iki dönüşümleri gelen kapsayıcı içinde çizilen öğeleri için uygulanır. Kapsayıcının dönüşümü uygulanan ilk ve dönüştürmeyi olacaktır <xref:System.Drawing.Graphics> nesne ikinci uygulanır. Kapsayıcının kırpma bölgeleri ayarlarsanız ve <xref:System.Drawing.Graphics> nesne öğesinden kapsayıcısının içinde çizilen öğeleri kırpma iki bölgeleri kesişimi ile kırpılarak.  
  
## <a name="quality-settings-in-nested-containers"></a>İç içe geçmiş kapsayıcılar kalite ayarları  
 Kalite ayarları (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>vb.), iç içe geçmiş kapsayıcılar toplu değildir; bunun yerine, kapsayıcı kalite ayarlarını geçici olarak kalite ayarlarını değiştirin. bir <xref:System.Drawing.Graphics> nesne. Yeni bir kapsayıcı oluşturduğunuzda, bu kapsayıcı için kalite ayarı varsayılan değerlere ayarlanır. Örneğin, sahip olduğunuz varsayalım. bir <xref:System.Drawing.Graphics> yumuşatma modu nesnesiyle <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Bir kapsayıcı oluşturduğunuzda, kapsayıcı içinde yumuşatma modu modu düzgünleştirme varsayılandır. Kapsayıcının yumuşatma modu ayarlamak ücretsizdir ve gelen kapsayıcı içinde çizilen öğelerde ayarladığınız modu göre çizileceğini. Çağrısından sonra çizilen öğeleri <xref:System.Drawing.Graphics.EndContainer%2A> göre yumuşatma moduna çizilmiş (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) olduğu yerde çağırmadan önce <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>İç içe geçmiş kapsayıcılar birkaç katmanı  
 Bir kapsayıcı içinde bunlarla sınırlı olmayan bir <xref:System.Drawing.Graphics> nesne. Gerçek koordinat dönüştürmesini, kırpma bölgesini ve her birinin bu iç içe geçmiş kapsayıcılar kalite ayarlarını belirtin ve önceki her iç içe veya bir dizi kapsayıcıları oluşturabilirsiniz. En içteki kapsayıcı içinde çizim yöntemden çağırırsanız, dönüştürmeleri en içteki kapsayıcı ile başlayıp en dıştaki kapsayıcıda sırasıyla uygulanır. Gelen en içteki kapsayıcısının içinde çizilen öğeleri tüm kırpma bölgeler kesişimini tarafından kırpılır.  
  
 Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Graphics> nesne ve onun metin işleme ipucu ayarlar <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod, bir iç içe iki kapsayıcı oluşturur. Dış kapsayıcının metin işleme ipucu kümesine <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, ve metin işleme ipucu iç kapsayıcısı kümesine <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod üç dizeyi çizer: iç kapsayıcısı, bir dış kapsayıcısından ve birinden diğerine <xref:System.Drawing.Graphics> nesnenin kendisi.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Aşağıdaki çizim üç dizeyi gösterir. İç kapsayıcısı'ndan ve çizilmiş dizeleri <xref:System.Drawing.Graphics> nesne tarafından düzgünleştirme düzleştirilir. Dış kapsayıcıdan çizilmiş dize tarafından düzgünleştirme çünkü düzleştirilmiş değil <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![İç içe geçmiş kapsayıcılar](./media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics>
- [Bir Grafik Nesnesinin Durumunu Yönetme](managing-the-state-of-a-graphics-object.md)
