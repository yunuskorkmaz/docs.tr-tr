---
title: Genel ve Yerel Dönüştürmeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955185"
---
# <a name="global-and-local-transformations"></a>Genel ve Yerel Dönüştürmeler
Genel dönüşüm, belirli <xref:System.Drawing.Graphics> bir nesne tarafından çizilen her öğe için geçerli olan dönüşümdir. Buna karşılık, yerel bir dönüşüm, çizilecek belirli bir öğe için geçerli olan dönüşümdir.  
  
## <a name="global-transformations"></a>Genel dönüşümler  
 Genel bir dönüşüm oluşturmak için, bir <xref:System.Drawing.Graphics> nesnesi oluşturun ve sonra <xref:System.Drawing.Graphics.Transform%2A> özelliğini değiştirin. <xref:System.Drawing.Graphics.Transform%2A> Özelliği bir<xref:System.Drawing.Drawing2D.Matrix> nesnesidir, bu nedenle herhangi bir afin dönüştürme dizisini tutabilir. <xref:System.Drawing.Graphics.Transform%2A> Özelliğinde depolanan dönüştürmeye dünya dönüşümü denir. <xref:System.Drawing.Graphics.RotateTransform%2A> <xref:System.Drawing.Graphics.MultiplyTransform%2A> <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics.ScaleTransform%2A>Sınıfı, bileşik dünya dönüşümü oluşturmak için çeşitli yöntemler sağlar:,, ve. <xref:System.Drawing.Graphics> Aşağıdaki örnek üç kez elips çizer: bir dünya dönüşümü oluşturmadan önce ve sonrasında bir kez. Dönüştürme ilk olarak y yönünde 0,5 faktörüyle ölçeklenirken, x yönünde 50 birimi çevirir ve sonra 30 derece döndürür.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Aşağıdaki çizimde, dönüşümde yer alan matrisler gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
> Yukarıdaki örnekte, elips, istemci alanının sol üst köşesinde bulunan koordinat sisteminin kaynağı hakkında döndürülür. Bu, elips kendi Merkezi hakkında döndürmeden farklı bir sonuç üretir.  
  
## <a name="local-transformations"></a>Yerel dönüşümler  
 Yerel bir dönüşüm, çizilecek belirli bir öğe için geçerlidir. Örneğin, bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi, bu yolun <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> veri noktalarını dönüştürmenizi sağlayan bir yönteme sahiptir. Aşağıdaki örnek, dönüşüm olmadan bir dikdörtgen ve bir döndürme dönüştürmesi içeren bir yol çizer. (Dünya dönüştürmesinin olmadığını varsayın.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Çeşitli sonuçlara ulaşmak için dünya dönüşümünü yerel dönüşümlerle birleştirebilirsiniz. Örneğin, koordinat sistemini değiştirmek ve yeni koordinat sisteminde çizilen nesneleri döndürmek ve ölçeklendirmek için yerel dönüştürmeleri kullanmak üzere dünya dönüşümünü kullanabilirsiniz.  
  
 İstemci alanının sol kenarından, istemci alanının en üstünden 150 piksel olan bir koordinat sisteminin kaynak 200 piksel olduğunu varsayalım. Ayrıca, ölçü biriminin sağ ve y eksenini işaret eden x ekseni ile piksel olmasını istediğinizi varsayın. Varsayılan koordinat sisteminde, aşağı işaret eden y ekseni bulunur, bu nedenle yatay eksen genelinde bir yansıma gerçekleştirmeniz gerekir. Aşağıdaki çizimde bu tür bir yansımanın matrisi gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Ardından, doğru ve 150 birim için çeviri 200 birimleri gerçekleştirmeniz gerektiğini varsayın.  
  
 Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnenin Dünya dönüşümünü ayarlayarak yalnızca açıklanan koordinat sistemini belirler.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Aşağıdaki kod (önceki örnekte yer alan), yeni koordinat sisteminin başlangıcına sol alt köşesine sahip tek bir dikdörtgenden oluşan bir yol oluşturur. Dikdörtgen yerel dönüşümle ve bir kez yerel dönüşümle bir kez doldurulur. Yerel dönüşüm, 2 faktörüyle bir yatay ölçeklendirmeden ve sonrasında 30 derecelik bir dönüşden oluşur.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Aşağıdaki çizimde, yeni koordinat sistemi ve iki dikdörtgen gösterilmektedir.  
  
 ![Dönüşümler](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)
