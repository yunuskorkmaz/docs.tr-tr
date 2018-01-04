---
title: "Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]otomatik olarak, hangi performans azalır çizerken görüntü ölçeklendirme. Alternatif olarak, hedef dikdörtgenin boyutlarını geçirerek görüntüsü ölçeklendirme denetleyebilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.  
  
 Aşağıdaki örnek, çağrısı <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi belirtir. bir sol üst köşesindeki (50, 30) ancak hedef dikdörtgen belirtmiyor.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Bu kolay sürümü olsa da <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi gerekli bağımsız değişken sayısı bakımından, mutlaka en etkin değil. Çözüm tarafından kullandıysanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (genellikle 96 inç başına nokta) depolanan çözümlemesi farklı <xref:System.Drawing.Image> nesnesi, sonra <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi görüntü ayarlayacaktır. Örneğin, varsayalım bir <xref:System.Drawing.Image> nesnesi 216 piksel genişliği ve 72 inç başına nokta saklı yatay çözünürlük değerine sahiptir. 216/72 3, olduğundan <xref:System.Drawing.Graphics.DrawImage%2A> 96 inç başına nokta çözünürlükte 3 inç genişliğini sahip olması görüntü ölçeklendirir. Diğer bir deyişle, <xref:System.Drawing.Graphics.DrawImage%2A> 96 x 3 = 288 genişliğini içeren bir görüntü görüntüler piksel.  
  
 Ekran çözünürlüğünü 96 inç başına nokta farklı olsa bile [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ekran çözünürlüğünü 96 inç başına nokta değilmiş gibi ölçek görüntü büyük olasılıkla olur. Çünkü bir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> nesnesi bir cihaz bağlamı ile ilişkili olan ve ne zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu ekran çözünürlüğü için cihaz bağlamı olan genellikle gerçek ekran çözünürlüğünü bakılmaksızın 96 sorguları. Hedef dikdörtgende belirterek otomatik ölçeklendirmeyi önleyebilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki kez aynı resim çizer. İlk durumda, genişlik ve yükseklik hedef dikdörtgenin belirtilmedi ve otomatik olarak ölçeklendirilir. İkinci durumda, genişlik ve yükseklik (piksel cinsinden ölçülür) hedef dikdörtgenin genişliği ve yüksekliği orijinal görüntünün aynı olması için belirtilmiş. Aşağıdaki çizimde, iki kez çizilir resim göstermektedir.  
  
 ![Ölçeklendirilmiş doku](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Texture.jpg bir görüntü adı ve, sisteminizde geçerli yolu değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
