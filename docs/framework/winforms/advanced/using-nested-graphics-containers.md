---
title: "İç İçe Grafik Kapsayıcılarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10c5a1b077e4339f17093e5eb935416bb1ae3d1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-nested-graphics-containers"></a>İç İçe Grafik Kapsayıcılarını Kullanma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]geçici olarak değiştirin veya durumda parçası büyütmek için kullanabileceğiniz kapsayıcıları sağlayan bir <xref:System.Drawing.Graphics> nesnesi. Bir kapsayıcı oluşturmanız <xref:System.Drawing.Graphics.BeginContainer%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi. Çağırabilirsiniz <xref:System.Drawing.Graphics.BeginContainer%2A> art arda iç içe geçmiş kapsayıcılar oluşturmak için. Her çağrı <xref:System.Drawing.Graphics.BeginContainer%2A> çağrısıyla eşleştirilmelidir <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>İç içe geçmiş kapsayıcılar dönüşümler  
 Aşağıdaki örnekte bir <xref:System.Drawing.Graphics> nesne ve içindeki bir kapsayıcı <xref:System.Drawing.Graphics> nesnesi. Dünya dönüşümü <xref:System.Drawing.Graphics> nesnesidir x yönünde 100 çeviri birimleri ve y yönünde 80 birimlerinde. Dünya dönüşümü kapsayıcısının 30 derecelik döndürme ' dir. Kod arama yapar `DrawRectangle(pen, -60, -30, 120, 60)` iki kez. İlk çağrıda <xref:System.Drawing.Graphics.DrawRectangle%2A> içinde kapsayıcı; diğer bir deyişle, çağrıları Between çağrıdır <xref:System.Drawing.Graphics.BeginContainer%2A> ve <xref:System.Drawing.Graphics.EndContainer%2A>. İkinci çağrı <xref:System.Drawing.Graphics.DrawRectangle%2A> çağrısından sonra olan <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Önceki kodda, dünya dönüşümü kapsayıcısının (dönüş) ve ardından dünya dönüşümü göre ilk gelen kapsayıcısı içindeki çizilmiş dikdörtgen dönüştürüldükten <xref:System.Drawing.Graphics> nesne (çevirisi). Gelen kapsayıcı dışında çizilmiş dikdörtgen yalnızca dünya dönüşümü tarafından dönüştürüldüğünde <xref:System.Drawing.Graphics> nesne (çevirisi). Aşağıdaki çizimde iki dikdörtgen gösterir.  
  
 ![İç içe geçmiş kapsayıcılar](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>İç içe geçmiş kapsayıcılar kırpma  
 Aşağıdaki örnekte nasıl iç içe geçmiş kapsayıcılar gösteren kırpma bölgeleri tanıtıcı. Kod oluşturur bir <xref:System.Drawing.Graphics> nesne ve içindeki bir kapsayıcı <xref:System.Drawing.Graphics> nesnesi. Kırpma bölgesini <xref:System.Drawing.Graphics> nesne dikdörtgen ve kırpma bölgesinin kapsayıcısının elips. Kod iki çağrılar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi. İlk çağrıda <xref:System.Drawing.Graphics.DrawLine%2A> kapsayıcı ve ikinci çağrısı içinde <xref:System.Drawing.Graphics.DrawLine%2A> kapsayıcıdır dışında (çağrısından sonra <xref:System.Drawing.Graphics.EndContainer%2A>). İlk satırı iki kırpma bölgeleri kesişimi ile kırpılır. İkinci satır yalnızca dikdörtgen kırpma bölgesini tarafından kırpılmış <xref:System.Drawing.Graphics> nesnesi.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Aşağıdaki çizimde iki kırpılmış satır gösterir.  
  
 ![İç içe kapsayıcı](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 İki önceki örneklerde görüldüğü gibi dönüşümler ve kırpma bölgeleri içinde iç içe geçmiş kapsayıcılar birbirinin yerine kullanılabilir. Kapsayıcının world dönüşümleri ayarlarsanız ve <xref:System.Drawing.Graphics> nesnesi, her iki dönüşümleri gelen kapsayıcısı içindeki çizilmiş öğeleri uygulanacak. Kapsayıcı dönüşümü uygulanan ilk ve dönüşümü olacaktır <xref:System.Drawing.Graphics> nesne ikinci uygulanır. Kapsayıcı kırpma bölgeleri ayarlarsanız ve <xref:System.Drawing.Graphics> nesne öğesinden kapsayıcısı içindeki çizilmiş öğeleri iki kırpma bölgeleri kesişimi ile kırpılmış.  
  
## <a name="quality-settings-in-nested-containers"></a>İç içe geçmiş kapsayıcılar kalite ayarları  
 Kalite ayarlarını (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>vb.) içinde iç içe geçmiş kapsayıcılar toplu değildir; bunun yerine, kapsayıcının kalite ayarlarını kalite ayarlarını geçici olarak değiştirmek bir <xref:System.Drawing.Graphics> nesnesi. Yeni bir kapsayıcı oluşturduğunuzda, bu kapsayıcı için kalite ayarlarını varsayılan değerlerine ayarlanır. Örneğin, sahip olduğunuz varsayalım bir <xref:System.Drawing.Graphics> yumuşatma modu nesnesiyle <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Bir kapsayıcı oluşturduğunuzda, kapsayıcı içinde yumuşatma mod modu düzgünleştirme varsayılandır. Kapsayıcının yumuşatma modu ayarlamak ücretsiz ve gelen kapsayıcısı içindeki çizilmiş herhangi bir öğeyi ayarladığınız modu göre çizileceğini. Çağrısından sonra çizilmiş öğeleri <xref:System.Drawing.Graphics.EndContainer%2A> göre yumuşatma modu çizileceğini (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) çağırmadan önce yerinde olduğu <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>İç içe geçmiş kapsayıcılar birkaç katmandan  
 Bir kapsayıcıda bunlarla sınırlı değildir bir <xref:System.Drawing.Graphics> nesnesi. Dünya dönüşümü, kırpma bölgesinin ve her birinin bu iç içe geçmiş kapsayıcılar kalite ayarlarını belirtebilirsiniz ve her önceki iç içe geçmiş veya bir dizi kapsayıcıları oluşturabilirsiniz. Çizim bir yönteminden en içteki kapsayıcı içinde çağırırsanız, dönüştürmeleri en içteki kapsayıcı ile başlayıp en dıştaki kapsayıcıda sırasıyla uygulanır. Gelen en içteki kapsayıcısı içindeki çizilmiş öğeleri tüm kırpma bölgeleri kesişimi ile kırpılır.  
  
 Aşağıdaki örnekte bir <xref:System.Drawing.Graphics> nesne ve onun metin oluşturma ipucu ayarlar <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod bir iç içe iki kapsayıcı oluşturur. Metin oluşturma ipucu dış kapsayıcısının kümesine <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, ve iç kapsayıcısının metin oluşturma ipucu kümesine <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod üç dizeleri çizer: iç kapsayıcı, bir dış kapsayıcısından ve birinden diğerine <xref:System.Drawing.Graphics> nesnesinin kendisi.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Aşağıdaki çizim üç dizeleri gösterir. Gelen ve giden iç kapsayıcısından çizilmiş dizeleri <xref:System.Drawing.Graphics> nesnesi tarafından düzgünleştirme düzleştirilmiş. Dış kapsayıcıdan çizilmiş dizesi tarafından düzgünleştirme çünkü düzleştirilmiş değil <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği ayarlanmış <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![İç içe geçmiş kapsayıcılar](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics>  
 [Bir grafik nesnesinin durumunu yönetme](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
