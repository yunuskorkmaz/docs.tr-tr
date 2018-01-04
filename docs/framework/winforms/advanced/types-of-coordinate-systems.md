---
title: "Koordinat Sistemi Türleri"
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
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a>Koordinat Sistemi Türleri
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]üç koordinat alanları kullanır: world, sayfa ve aygıt. Dünya koordinat belirli bir grafik world model oluşturmak için kullanılan koordinatları ve .NET Framework yöntemlere geçirmek koordinatları. Sayfa koordinat bir form veya denetim gibi bir çizim yüzeyini tarafından kullanılan koordinat sistemi bakın. Cihaz koordinat ekran veya kağıt gibi sonuna çizilen bir fiziksel aygıt tarafından kullanılan koordinatlar belirlenir. Arama yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, geçişi için noktaları <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi —`(0, 0)` ve `(160, 80)`— dünya koordinat alanındadır. Önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgi ekranda çizebilirsiniz, bir dizi dönüştürmeyi koordinatları geçirin. Dünya dönüşümü adlı bir dönüşüm world koordinatları sayfa koordinatlara dönüştürür ve sayfa dönüşümü adlı başka bir dönüşüm sayfa koordinatları aygıt koordinatlara dönüştürür.  
  
## <a name="transforms-and-coordinate-systems"></a>Dönüşümler ve koordinat sistemleri  
 Sol üst köşe yerine istemci alanını gövdesinde kaynağına sahip bir koordinat sistemi çalışmak istediğinizi varsayalım. Örneğin, istemci alanını sol kenarından 100 piksel ve istemci alanını üstünden 50 piksel olması için kaynak istediğinizi varsayalım. Aşağıdaki çizimde, bu tür bir koordinat sistemi gösterir.  
  
 ![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Arama yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, aşağıdaki çizimde gösterilen satır alın.  
  
 ![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Üç koordinat alanları, satır uç noktalarına koordinatlarını aşağıdaki gibidir:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (160, 80)|  
|Sayfa|(100, 50) için (260, 130)|  
|Cihaz|(100, 50) için (260, 130)|  
  
 Sayfa koordinat istemci alanını sol üst köşesinde kaynağına sahip olduğunu unutmayın; Bu durumda her zaman olacaktır. Ayrıca ölçü piksel olduğundan, cihaz koordinatları sayfa koordinatları ile aynı olduğunu unutmayın. Piksel (örneğin, inç) dışında bir şey için ölçü ayarlarsanız, aygıt koordinatları sayfa koordinatları farklı olacaktır.  
  
 Dünya koordinat sayfa koordinatlara eşler, dünya dönüşümü tutulur <xref:System.Drawing.Graphics.Transform%2A> özelliği <xref:System.Drawing.Graphics> sınıfı. Önceki örnekte, dünya dönüşümü x yönünde çeviri 100 birimlerinde y yönünde 50 birime ise. Aşağıdaki örnek, dünya dönüşümü ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından kullanan <xref:System.Drawing.Graphics> Yukarıdaki çizimde gösterilen çizgi çizmek için nesnesi:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Sayfa dönüşümü sayfa koordinatları aygıt koordinatlara eşler. <xref:System.Drawing.Graphics> SAX <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> sayfa dönüşümü düzenleme özellikleri. <xref:System.Drawing.Graphics> Sınıfı iki salt okunur özellikler sağlar <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>, yatay ve dikey inç başına nokta görüntü aygıtının incelenmesinin.  
  
 Kullanabileceğiniz <xref:System.Drawing.Graphics.PageUnit%2A> özelliği <xref:System.Drawing.Graphics> piksel dışında bir ölçü belirlemek için sınıf.  
  
> [!NOTE]
>  Ayarlayamazsınız <xref:System.Drawing.Graphics.PageUnit%2A> özelliğine <xref:System.Drawing.GraphicsUnit.World>, bu fiziksel bir birim değil ve bir özel durumuna neden olur.  
  
 Aşağıdaki örnek bir satırından çizer (0, 0) için (2, 1), burada noktası (2, 1), 2 inç sağına ve aşağı 1 inç noktasından (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Kalem yapısı oluştururken kalem genişliği belirtmezseniz, önceki örnekte bir inç geniş bir çizgi çizin. İkinci bağımsız değişkeni kalem genişliği belirtebilirsiniz <xref:System.Drawing.Pen> Oluşturucusu:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Görüntü aygıtı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz, önceki örnekte satırının bitiş noktaları aşağıdaki koordinatları üç koordinat alanlarında vardır:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (2, 1)|  
|Sayfa|(0, 0) için (2, 1)|  
|Cihaz|(0, 0, için (192, 96)|  
  
 Dünya koordinat kökeni istemci alanını sol üst köşesinde olduğundan, sayfa koordinatları world koordinatları ile aynı olduğunu unutmayın.  
  
 Çeşitli efektler elde etmek için world ve sayfa dönüştürmeleri birleştirebilirsiniz. Örneğin, inç ölçü birimi kullanmak istediğiniz ve istemci alanını 1/2 inç istemci alanının üst ve sol kenarından 2 inç olacak şekilde, koordinat sistemi kökeni istediğinizi varsayalım. Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesne ve bir satırından çizer (0, 0) için (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Aşağıdaki çizimde satır ve koordinat sistemi gösterir.  
  
 ![Koordinat sistemi](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Görüntü aygıtı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz, önceki örnekte satırının bitiş noktaları aşağıdaki koordinatları üç koordinat alanlarında vardır:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (2, 1)|  
|Sayfa|(2, 0,5) için (4, 1.5)|  
|Cihaz|(192, 48) için (384, 144)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koordinat Sistemleri ve Dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [Dönüşümlerin Matrisle Temsili](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
