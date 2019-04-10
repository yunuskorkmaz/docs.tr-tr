---
title: 'Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 78fc498b0689026fb74ec0c422948c1879495560
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342862"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve bu görüntüleri düzenleme için sınıflar. <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> 32 bit bir sayı nesneleri depolamak her piksel rengi: 8 bitlik her kırmızı, yeşil, mavi ve alfa için. Her biri dört bileşen, 0 ile hiçbir yoğunluğu ve tam bir yoğunluğu temsil eden 255 temsil eden 0 ile 255 arasında bir sayıdır. Alfa bileşeni rengini, saydamlığını belirtir: 0 tamamen saydamdır ve tam opak 255'tir.  
  
 4 bölütlü (kırmızı, yeşil, mavi, alfa) biçiminde bir renk vektördür. Örneğin, (0, 255, 0, 255) renk vektör kırmızı veya mavi olmayan, ancak tam yoğunlukta yeşil sahip donuk bir rengi temsil eder.  
  
 Renkleri temsil eden başka bir kural 1 sayısı için tam yoğunluğu kullanır. Bu kuralı kullanarak, önceki paragrafta açıklanan rengi (0, 1, 0, 1) vektörü ile gösterilir. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renk dönüştürmeleri gerçekleştirdiğinde kuralı 1 tam yoğunluğu kullanılır.  
  
 Renk vektör 4 x 4 matris tarafından çarpılarak renk vektörlerinin doğrusal Dönüşümler (döndürme, ölçeklendirme ve benzeri) uygulayabilirsiniz. Ancak, bir çeviri (doğrusal) gerçekleştirmek için 4 x 4 matris kullanamazsınız. İşlevsiz beşinci koordinat (örneğin, 1 sayı) her renk vektörleri eklerseniz, herhangi bir birleşimini doğrusal dönüşümler ve çevirileri uygulamak için 5 × 5 matris kullanabilirsiniz. Bir çeviri tarafından izlenen bir doğrusal dönüştürme oluşan bir dönüştürme afin bir dönüştürme çağrılır.  
  
 Örneğin, rengi (0.2, 0.0, 0.4, 1.0) ile başlatın ve aşağıdaki dönüştürmeleri istediğinizi varsayalım:  
  
1. Çift kırmızı bileşeni  
  
2. 0,2 kırmızı, yeşil ve mavi bileşenlere ekleme  
  
 Aşağıdaki matris çarpım dönüşümleri çiftinin listelenen sırayla gerçekleştirir.  
  
 ![Yeniden renklendirme](./media/recoloring01.gif "recoloring01")  
  
 Renk Matrisi öğelerini (sıfır tabanlı) satır ve ardından sütun tarafından dizine eklenir. Örneğin, üçüncü sütunda matris M ve beşinci satır girişi M [4] [2] belirtilir.  
  
 5 × 5 kimlik matrisi (aşağıda gösterilmiştir) üzerinde çapraz 1s ve her yerde başka 0s sahiptir. Bir renk vektör tarafından kimlik matrisi çarpın, renk vektör değiştirmez. Bir renk dönüştürme matrisini oluşturmak için bir kimlik matris başlatmak ve istenen dönüşümü üretir küçük bir değişiklik yapmak için yoludur.  
  
 ![Yeniden renklendirme](./media/recoloring02.gif "recoloring02")  
  
 Matrisler ve dönüşümleri daha ayrıntılı bir açıklaması için bkz. [koordinat sistemleri ve dönüştürmeler](coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm bir renk (0.2, 0.0, 0.4, 1.0) ve önceki paragrafta açıklanan dönüştürme geçerli bir görüntüsünü alır.  
  
 Aşağıdaki çizimde, sol taraftaki özgün görüntü ve dönüştürülen görüntü sağ tarafta gösterir.  
  
 ![Renkleri](./media/colortrans1.png "colortrans1")  
  
 Aşağıdaki örnek kodda, yeniden renklendirme gerçekleştirmek için aşağıdaki adımları kullanır:  
  
1. Başlatma bir <xref:System.Drawing.Imaging.ColorMatrix> nesne.  
  
2. Oluşturma bir <xref:System.Drawing.Imaging.ImageAttributes> nesne ve geçirin <xref:System.Drawing.Imaging.ColorMatrix> nesnesini <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesne.  
  
3. Geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Resimleri Yeniden Renklendirme](recoloring-images.md)
- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
