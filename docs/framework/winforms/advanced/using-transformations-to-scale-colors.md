---
title: Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 6cfe90cef42086672990c45c99961db3d29c3ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525973"
---
# <a name="using-transformations-to-scale-colors"></a>Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma
Ölçeklendirme dönüştürme, bir veya daha fazla bir sayıyla dört renk bileşenleri çarpar. Ölçeklendirme temsil eden renk matrisi girişi aşağıdaki tabloda verilmiştir.  
  
|Ölçeklendirilmesi bileşeni|Matris giriş|  
|----------------------------|------------------|  
|kırmızı|[0][0]|  
|Yeşil|[1][1]|  
|Mavi|[2][2]|  
|Alfa|[3][3]|  
  
## <a name="scaling-one-color"></a>Bir renk ölçeklendirme  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi. Ardından kod, her piksel mavi bileşeninin görüntüde 2 faktörüyle ölçeklendirir. Özgün görüntüsüne dönüştürülmüş yansımasının yanında çizilir.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Aşağıdaki çizimde özgün resim soldaki ve ölçeklendirilmiş görüntü sağ tarafta gösterir.  
  
 ![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")  
  
 Aşağıdaki tabloda, önce ve sonra mavi ölçeklendirme dört Çubuklar için renk vektörlerinin listeler. Dördüncü renk çubuğu mavi bileşeni için 0,6 0,8 oluştu unutmayın. Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu yalnızca kesirli kısmını korur. Örneğin, (2)(0.8) 1.6, = ve kesirli 1.6 0,6 bir parçasıdır. Yalnızca kesir bölümünü korunuyor sonucu her zaman [0, 1] aralığında olmasını sağlar.  
  
|Özgün|Genişletilmiş|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Birden çok renkleri ölçekleme  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi. Ardından kod her piksel kırmızı, yeşil ve mavi bileşenlerinin görüntüde ölçeklendirir. Kırmızı bileşenleri yüzde 25'i ölçeklenir, yeşil bileşenleri yüzde 35 ' ölçeklenir ve mavi bileşenleri yüzde 50 ' ölçeklenir.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Aşağıdaki çizimde özgün resim soldaki ve ölçeklendirilmiş görüntü sağ tarafta gösterir.  
  
 ![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")  
  
 Aşağıdaki tabloda, önce ve sonra kırmızı, yeşil ve mavi ölçeklendirme dört Çubuklar için renk vektörlerinin listeler.  
  
|Özgün|Genişletilmiş|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)
