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
ms.openlocfilehash: ea4abc38968b929412945cddaca3ca3fe6f377d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707436"
---
# <a name="using-transformations-to-scale-colors"></a>Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma
Ölçekleme dönüşümü bir veya daha fazla bir sayıyla dört renk bileşenlerine çarpar. Ölçeklendirme temsil eden renk matrisi girişleri aşağıdaki tabloda verilmiştir.  
  
|Bileşen ölçeklendirilmesi|Matris giriş|  
|----------------------------|------------------|  
|Kırmızı|[0][0]|  
|Yeşil|[1][1]|  
|Mavi|[2][2]|  
|Alpha|[3][3]|  
  
## <a name="scaling-one-color"></a>Bir renk ölçeklendirme  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi. Ardından kod, her pikselin mavi bileşeni görüntüde 2 faktörüyle ölçeklendirir. Özgün resmin dönüştürülmüş görüntünün yanı sıra çizilir.  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 Aşağıdaki çizimde, sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü sağ tarafta gösterir.  
  
 ![Renkleri ölçeklendirmek](./media/colortrans3.png "colortrans3")  
  
 Aşağıdaki tabloda önceki ve sonraki mavi ölçeklendirme dört Çubuklar için rengi vektörleri listeler. Dördüncü renk çubuğu mavi bileşeni 0.8 0,6 için gönderilmediğine dikkat edin. Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu yalnızca kesirli kısmını korur. Örneğin, (2)(0.8) 1.6, = ve kesirli 1.6 0,6 parçasıdır. Yalnızca kesirli bölümü koruma sonucu her zaman [0, 1] aralığında olmasını sağlar.  
  
|Özgün|Ölçeği genişletilmiş|  
|--------------|------------|  
|(0.4, 0.4, 0.4, 1)|(0.4, 0.4, 0.8, 1)|  
|(0.4, 0.2, 0.2, 1)|(0.4, 0.2, 0.4, 1)|  
|(0.2, 0.4, 0.2, 1)|(0.2, 0.4, 0.4, 1)|  
|(0.4, 0.4, 0.8, 1)|(0.4, 0.4, 0.6, 1)|  
  
## <a name="scaling-multiple-colors"></a>Birden çok renkleri ölçekleme  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi. Ardından kod her piksel kırmızı, yeşil ve mavi bileşenlerinin görüntüde ölçeklendirir. Kırmızı bileşenleri yüzde 25 ölçeklenir yeşil bileşenleri yüzde 35 ölçeklenir ve mavi bileşenlerinin yüzde 50 ölçeklenir.  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 Aşağıdaki çizimde, sol taraftaki özgün görüntü ve ölçeklendirilmiş görüntü sağ tarafta gösterir.  
  
 ![Renkleri ölçeklendirmek](./media/colortrans4.png "colortrans4")  
  
 Aşağıdaki tabloda dört Çubuklar için rengi vektörleri önce ve sonra kırmızı, yeşil ve mavi ölçeklendirme listeler.  
  
|Özgün|Ölçeği genişletilmiş|  
|--------------|------------|  
|(0.6, 0.6, 0.6, 1)|(0.45, 0.39, 0.3, 1)|  
|(0, 1, 1, 1)|(0, 0.65, 0.5, 1)|  
|(1, 1, 0, 1)|(0.75, 0.65, 0, 1)|  
|(1, 0, 1, 1)|(0.75, 0, 0.5, 1)|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Görüntüleri Yeniden Renklendirme](recoloring-images.md)
