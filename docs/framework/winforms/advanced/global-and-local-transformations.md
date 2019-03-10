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
ms.openlocfilehash: 07ef61e3a41448f051fb9b7da2cfd91d7cbf26b5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711856"
---
# <a name="global-and-local-transformations"></a>Genel ve Yerel Dönüştürmeler
Her bir öğe tarafından çizilen uygulandığı bir dönüştürme genel bir dönüşümdür bir verilen <xref:System.Drawing.Graphics> nesne. Buna karşılık, yerel bir dönüştürme çizilecek belirli bir ögeye uygulanan bir dönüşümdür.  
  
## <a name="global-transformations"></a>Genel dönüşümleri  
 Genel dönüşümü oluşturmak için oluşturmak bir <xref:System.Drawing.Graphics> nesne ve işlemek, <xref:System.Drawing.Graphics.Transform%2A> özelliği. <xref:System.Drawing.Graphics.Transform%2A> Özelliği bir <xref:System.Drawing.Drawing2D.Matrix> afin dönüşümler herhangi bir dizi içerebileceği için nesne. Dönüştürme depolanan <xref:System.Drawing.Graphics.Transform%2A> özelliği gerçek koordinat dönüştürmesini çağrılır. <xref:System.Drawing.Graphics> Sınıfı bir bileşik gerçek koordinat dönüştürmesini oluşturmak için çeşitli yöntemler sağlar: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, ve <xref:System.Drawing.Graphics.TranslateTransform%2A>. Aşağıdaki örnek iki kez bir elips çizer: Gerçek koordinat dönüştürmesini ve sonra bir kez'ı oluşturmadan önce bir kez. Dönüştürme ilk 0,5 y yönünde faktörüyle ölçeklenen sonra 50 birim x yönünde çevirir ve ardından 30 derece döndürür.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Aşağıdaki çizim matrislerde dönüşümü katılan gösterir.  
  
 ![Dönüşümler](./media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  Önceki örnekte, üç nokta istemci alanını sol üst köşesine gelecek koordinat sistemini kaynağı hakkında döndürülür. Bu, kendi Merkezi hakkında elips döndürme değerinden farklı bir sonuç oluşturur.  
  
## <a name="local-transformations"></a>Yerel dönüştürmeler  
 Yerel bir dönüştürme çizilecek belirli bir öğeyi uygular. Örneğin, bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesinin bir <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> yol veri noktalarını dönüştürmenizi sağlayan yöntemi. Aşağıdaki örnek, döndürme dönüşümü yoluyla ve hiçbir dönüşüm bir dikdörtgen çizer. (Hiçbir gerçek koordinat dönüştürmesini olduğu varsayılmaktadır.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Gerçek koordinat dönüştürmesini çeşitli sonuçlar elde etmek için yerel dönüşümler ile birleştirebilirsiniz. Örneğin, gerçek koordinat dönüştürmesini koordinat sistemini gözden geçirin ve yeni koordinat sisteminde çizilen nesneleri döndürme ve yerel dönüştürmeler kullanmak için kullanabilirsiniz.  
  
 İstemci alanın sol kenarından kendi kaynak 200 piksel ve istemci alanının üst 150 piksel olan bir koordinat sistemini istediğinizi varsayalım. Ayrıca, sağa ve y ekseni yukarıyı gösteren x ekseni ile piksel olması için ölçü birimini istediğinizi varsayalım. Yatay eksende bir yansıma gerçekleştirmeniz gereken şekilde varsayılan koordinat sistemi aşağıyı, y ekseni sahiptir. Aşağıdaki çizimde, böyle bir yansıma matrisini gösterir.  
  
 ![Dönüşümler](./media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Ardından, bir çeviri 200 birimleri sağa ve aşağı 150 birimleri gerçekleştirmeniz gereken varsayılır.  
  
 Aşağıdaki örnek, gerçek koordinat dönüştürmesini ayarlayarak açıklanmış koordinat sistemini kurar bir <xref:System.Drawing.Graphics> nesne.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 (Önceki örnekte sonunda yer) aşağıdaki kod, yeni koordinat sistemi kaynağını sol alt köşede ile tek bir dikdörtgen oluşan bir yol oluşturur. Dikdörtgen bir kez yerel hiçbir dönüştürme ve bir kez yerel bir dönüşüm ile doldurulur. Yerel dönüşümü bir yatay bir 30 derece döndürme tarafından izlenen 2'ın ölçeklendirme oluşur.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Aşağıdaki çizim, yeni koordinat sistemini ve iki dikdörtgenler gösterir.  
  
 ![Dönüşümler](./media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)
