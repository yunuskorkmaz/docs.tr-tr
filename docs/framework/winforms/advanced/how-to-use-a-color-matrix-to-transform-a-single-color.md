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
ms.openlocfilehash: 741259fcf853c82dfd13b43edc92e50d8767887b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527410"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Nasıl yapılır: Tek Bir Rengi Dönüştürmek için Renk Matrisi Kullanma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar. <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> 32 bitlik bir sayı nesneleri depolamak her piksel rengi: 8 bit her kırmızı, yeşil, mavi ve alfa için. Dört bileşenlerinden her biri, 0-hiçbir yoğunluğu ve tam yoğunluğu temsil eden 255 temsil eden 0 ile 255 arasında bir sayıdır. Renk saydam alfa bileşeni belirtir: 0 tamamen saydamdır ve 255'tir tamamıyla opak.  
  
 Bir renk vektör 4 bölütlü (kırmızı, yeşil, mavi, alfa) biçiminde olur. Örneğin, renk vektör (0, 255, 0, 255) hiçbir kırmızı veya mavi sahiptir, ancak tam yoğunlukta yeşil sahip bir opak rengi temsil eder.  
  
 Renkleri temsil etmek için başka bir kuralı 1 numaralı tam yoğunluğu için kullanılır. Bu kuralı kullanarak, önceki paragrafta açıklanan rengi (0, 1, 0, 1) vektörü ile gösterilir. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renk dönüştürmeleri gerçekleştirdiğinde kuralı 1 tam yoğunluğu kullanılır.  
  
 Doğrusal Dönüşümler (döndürme, ölçeklendirme ve benzeri) 4 × 4 matris tarafından renk vektörlerinin çarparak renk vektörlerinin uygulayabilirsiniz. Ancak, bir çeviri (doğrusal) gerçekleştirmek için 4 × 4 matris kullanamazsınız. Her renk vektörlerinin kukla beşinci koordinat (örneğin, 1 sayı) eklerseniz, doğrusal dönüşümler ve çevirileri herhangi bir bileşimini uygulamak için 5 × 5 matris kullanabilirsiniz. Bir çeviri tarafından izlenen bir doğrusal dönüştürmesi oluşan bir dönüşüm afin dönüştürme adı verilir.  
  
 Örneğin, renk (0.2, 0.0, 0.4, 1.0) başlatın ve aşağıdaki dönüştürmeleri istediğinizi varsayalım:  
  
1.  Çift kırmızı bileşeni  
  
2.  Kırmızı, yeşil ve mavi bileşenlere 0.2 ekleme  
  
 Aşağıdaki matris çarpım dönüşümleri çiftinin listelenen sırayla gerçekleştirir.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")  
  
 Bir renk matrisi öğelerini (sıfır tabanlı) satır ve ardından sütun tarafından dizinlenir. Örneğin, beşinci satır ve üçüncü sütun matrisi M girişi M [4] [2] tarafından belirtilir.  
  
 5 × 5 kimlik matris (aşağıda gösterilen) 1'ler üzerinde çapraz ve 0'lar her yerde başka sahiptir. Bir renk vektör tarafından kimlik matris Çarp, renk vektör değiştirmez. Bir renk dönüştürme matrisi oluşturmak için bir kimlik matrisi başlatmak ve istenen dönüştürme üreten küçük değişiklikler yapmak için yoludur.  
  
 ![Yeniden renklendirme](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 Matrisleri ve dönüştürmeler daha ayrıntılı bir tartışma için bkz [koordinat sistemleri ve dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm bir renk (0.2, 0.0, 0.4, 1.0) ve önceki paragrafta açıklanan dönüştürmesi uygular bir görüntüsünü alır.  
  
 Aşağıdaki çizimde özgün resim soldaki ve dönüştürülen görüntünün sağ tarafta gösterir.  
  
 ![Renkleri](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 Aşağıdaki örnek kodda yeniden renklendirme gerçekleştirmek için aşağıdaki adımları kullanır:  
  
1.  Başlatma bir <xref:System.Drawing.Imaging.ColorMatrix> nesnesi.  
  
2.  Oluşturma bir <xref:System.Drawing.Imaging.ImageAttributes> nesne ve geçirin <xref:System.Drawing.Imaging.ColorMatrix> nesnesini <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi.  
  
3.  Geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüleri Yeniden Renklendirme](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Koordinat Sistemleri ve Dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
