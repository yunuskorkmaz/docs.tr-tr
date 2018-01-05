---
title: "Genel ve Yerel Dönüştürmeler"
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e8d05bd0c3e76d643d56b652c8849eef1045ea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="global-and-local-transformations"></a>Genel ve Yerel Dönüştürmeler
Genel bir dönüşüm tarafından çizilmiş her öğe için geçerli bir dönüşümü gerçekleşir bir verilen <xref:System.Drawing.Graphics> nesnesi. Buna karşılık, yerel bir dönüşüm çizilecek belirli bir öğeye uygulanan bir dönüşüm ' dir.  
  
## <a name="global-transformations"></a>Genel dönüşümleri  
 Genel dönüştürme oluşturmak için oluşturmak bir <xref:System.Drawing.Graphics> nesne ve sonra değiştirmek kendi <xref:System.Drawing.Graphics.Transform%2A> özelliği. <xref:System.Drawing.Graphics.Transform%2A> Özelliği bir <xref:System.Drawing.Drawing2D.Matrix> afin dönüşümler herhangi bir dizi tutabilir nesnesini. Dönüştürme depolanan <xref:System.Drawing.Graphics.Transform%2A> özelliği, dünya dönüşümü çağrılır. <xref:System.Drawing.Graphics> Sınıfı bileşik dünya dönüşümü oluşturmaya yönelik birkaç yöntem sağlar: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, ve <xref:System.Drawing.Graphics.TranslateTransform%2A>. Aşağıdaki örnekte iki kez elips çizilmiştir: Dünya dönüşümü ve sonra bir kez oluşturmadan önce bir kez. Dönüştürme y yönünde 0,5 faktörüyle ilk ölçeklendirir sonra 50 birim x yönünde çevirir ve 30 derece döndürür.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 Aşağıdaki çizimde matrisleri dönüştürme katılan gösterir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  Önceki örnekte, istemci alanını sol üst köşesinde olduğu koordinat sistemi kökeni hakkında elips döndürülür. Bu, kendi Merkezi hakkında elips döndürme daha farklı bir sonuç oluşturur.  
  
## <a name="local-transformations"></a>Yerel dönüştürmeler  
 Yerel bir dönüşüm çizilecek belirli bir öğeye uygular. Örneğin, bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> yol veri noktalarının dönüştürmenizi sağlar yöntemi. Aşağıdaki örnek, bir yol döndürme dönüşümü ve hiçbir dönüştürme bir dikdörtgen çizer. (Hiçbir dünya dönüşümü olduğu varsayılmaktadır.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Dünya dönüşümü çeşitli sonuçlar elde etmek için yerel dönüşümleri ile birleştirebilirsiniz. Örneğin, dünya dönüşümü koordinat sistemi gözden geçirin ve yerel dönüştürmeler döndürmek ve nesneler yeni koordinat sistemini çizilmiş ölçeklendirmek için kullanmak için kullanabilirsiniz.  
  
 Kendi kaynak 200 istemci alanını sol kenarından ve 150 pikseller yukarıdan istemci alanının sahip bir koordinat sistemi istediğinizi varsayalım. Ayrıca, sağa ve yukarıyı y ekseni işaret eden x ekseni ile piksel olması ölçü istediğinizi varsayalım. Varsayılan koordinat sistemi aşağıyı, y ekseni sahiptir, bu nedenle bir yansıma yatay eksende gerçekleştirmeniz gerekir. Aşağıdaki çizimde, bu tür bir yansıma matris gösterir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Ardından, bir çeviri 200 birimleri sağa ve aşağı 150 birimleri yapmanız gereken varsayalım.  
  
 Aşağıdaki örnek yeni dünya dönüşümü ayarı tanımlanan koordinat sistemi kurar bir <xref:System.Drawing.Graphics> nesnesi.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 Aşağıdaki kod (önceki örnekte sonunda yerleştirilmiş) kendi yeni koordinat sistemi kökeni sol alt köşede ile tek bir dikdörtgen oluşan bir yol oluşturur. Dikdörtgen bir kez hiçbir yerel dönüştürme ve bir kez yerel dönüştürme ile doldurulur. Bir yatay bir 30 derecelik döndürme ve ardından 2 faktörüyle ölçekleme yerel dönüştürme oluşur.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 Aşağıdaki çizimde, yeni koordinat sistemi ve iki dikdörtgen gösterir.  
  
 ![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koordinat Sistemleri ve Dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Yönetilen GDI+'da Dönüştürmeleri Kullanma](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
