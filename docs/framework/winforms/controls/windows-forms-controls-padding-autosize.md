---
title: 'İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Forms Denetimlerini Düzenleme'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987172"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>İzlenecek yol: Denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme

Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir. Visual Studio 'daki **Windows Form Tasarımcısı** , bunu gerçekleştirmek için size çok sayıda düzen aracı sağlar. En önemlileri <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A>, ve <xref:System.Windows.Forms.Control.AutoSize%2A> tüm Windows Forms Denetimlerinde bulunan özelliklerdir.

<xref:System.Windows.Forms.Control.Margin%2A> Özelliği, denetimin kenarlıklarından belirli bir uzaklıkta bulunan diğer denetimleri tutan denetimin etrafındaki boşluğu tanımlar.

Özelliği, denetimin içeriklerini (örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değeri) denetimin kenarlıklarından belirtilen uzaklıktan tutup denetimin içeriğini tutan bir denetimin iç kısmında yer alan alanı tanımlar. <xref:System.Windows.Forms.Control.Padding%2A>

Aşağıdaki çizim, <xref:System.Windows.Forms.Control.Padding%2A> bir denetimdeki ve <xref:System.Windows.Forms.Control.Margin%2A> özelliklerini gösterir.

![Windows Forms denetimleri için doldurma ve kenar boşluğu](./media/vs-winformpadmargin.gif)

Özelliği <xref:System.Windows.Forms.Control.AutoSize%2A> , bir denetime kendi içeriğini otomatik olarak boyutunu söylemektedir. Kendisini özgün <xref:System.Windows.Forms.Control.Size%2A> özelliğinin değerinden küçük olacak şekilde yeniden boyutlandıramaz ve <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değeri için hesaba sahip olur.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'da adlı `LayoutExample`bir **Windows uygulaması** projesi oluşturun.

2. **Windows Form Tasarımcısı**formunu seçin.

## <a name="set-margins-for-controls"></a>Denetimler için kenar boşluklarını ayarlama

<xref:System.Windows.Forms.Control.Margin%2A> Özelliğini kullanarak, denetimleriniz arasındaki varsayılan mesafeyi ayarlayabilirsiniz. Bir denetimi başka bir denetime kadar yakından taşıdığınızda, iki denetim için kenar boşluklarını gösteren bir anlık görüntü satırı görürsünüz. Taşıdığınız denetim, kenar boşlukları tarafından tanımlanan uzaklıktan de yaslıolur.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Kenar boşluğu özelliğini kullanarak formunuzdaki denetimleri düzenleme

1. <xref:System.Windows.Forms.Button> **Araç kutusundan** iki denetimi formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> Denetimlerden birini seçin ve neredeyse dokununcaya kadar, diğerine yakın hareket ettirin.

   Aralarında görüntülenen anlık görüntü çizgisini gözlemleyin. Bu uzaklık, iki denetimlerin <xref:System.Windows.Forms.Control.Margin%2A> değerlerinin toplamıdır. Taşıdığınız denetim bu uzaklığa yapışır. Ayrıntılar için bkz [. İzlenecek yol: Windows Forms denetimleri, snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)kullanarak düzenleme.

3. <xref:System.Windows.Forms.Control.Margin%2A> **Özellikler penceresinde** girişi genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliği **20**olarak ayarlayarak denetimlerden birinin özelliğinideğiştirin.<xref:System.Windows.Forms.Control.Margin%2A>

4. <xref:System.Windows.Forms.Button> Denetimlerden birini seçin ve diğerine yakın taşıyın.

   Kenar boşluğu değerlerinin toplamını tanımlayan anlık görüntü satırı daha uzundur ve denetimin diğer denetimden daha fazla mesafeye yaslanır.

5. <xref:System.Windows.Forms.Control.Margin%2A> **Özellikler penceresinde** girişi genişleterek ve <xref:System.Windows.Forms.Padding.Top%2A> özelliği **5**olarak ayarlayarak seçili denetimin özelliğinideğiştirin.<xref:System.Windows.Forms.Control.Margin%2A>

6. Seçili denetimi diğer denetimin altına taşıyın ve Snapın çizgisinin daha kısa olduğunu gözlemleyin. Seçili denetimi diğer denetimin soluna taşıyın ve Snapın değerinin 4. adımda gözlenen değeri koruduğunu gözlemleyin.

7. <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.Bottom%2A> <xref:System.Windows.Forms.Padding.Right%2A> <xref:System.Windows.Forms.Padding.All%2A> Özelliği,<xref:System.Windows.Forms.Padding.Top%2A>,,,,,,,,, özelliğinin herbirinifarklıdeğerlereayarlayabilirveyatümünü,özelliğiileaynıdeğereayarlayabilirsiniz.<xref:System.Windows.Forms.Padding.Left%2A>

## <a name="set-padding-for-controls"></a>Denetimler için doldurma ayarla

Uygulamanız için gereken kesin düzeni elde etmek için, denetimleriniz genellikle alt denetimler içerir. Alt denetimin kenarlığının üst denetimin kenarlığına yakınlığını belirtmek istediğinizde, üst denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini alt <xref:System.Windows.Forms.Control.Margin%2A> denetimin özelliği ile birlikte kullanın. Özelliği, bir denetimin içeriğinin (örneğin, bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) kenarlıklarına yakınlığını denetlemek için de kullanılır. <xref:System.Windows.Forms.Control.Padding%2A>

### <a name="arrange-controls-on-your-form-using-padding"></a>Doldurma kullanarak formunuzdaki denetimleri düzenleme

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. Denetimin özelliğinin değerini true olarak değiştirin. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A>

3. <xref:System.Windows.Forms.Control.Padding%2A> **Özellikler penceresinde** girişi genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **5**olarak ayarlayarak özelliğideğiştirin.<xref:System.Windows.Forms.Control.Padding%2A>

   Denetim, yeni doldurma için yer sağlamak üzere genişler.

4. <xref:System.Windows.Forms.GroupBox> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. Bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan denetime sürükleyin** <xref:System.Windows.Forms.GroupBox> . <xref:System.Windows.Forms.Button> Denetimi <xref:System.Windows.Forms.GroupBox> denetimin sağ alt köşesine doğru olarak konumlandırın.

   Denetim, denetimin alt ve sağ kenarlıklarına <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.GroupBox> yaklaşırsa görüntülenen anlık görüntü çizgilerini gözlemleyin. Bu ek çizgi, <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Button>özelliğine karşılık gelir.

5. <xref:System.Windows.Forms.Control.Padding%2A> **Özellikler** penceresinde girişigenişleterek<xref:System.Windows.Forms.Control.Padding%2A> ve **özelliği 20**olarak ayarlayarak denetiminözelliğinideğiştirin.<xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Padding.All%2A>

6. Denetim içindeki denetimi seçin ve merkezinin ortasına <xref:System.Windows.Forms.GroupBox>doğru taşıyın. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.GroupBox>

   Anlık görüntü çizgileri, <xref:System.Windows.Forms.GroupBox> denetimin kenarlıklarından daha fazla mesafede görünür. Bu <xref:System.Windows.Forms.Button> uzaklık, <xref:System.Windows.Forms.Control.Margin%2A> denetimin <xref:System.Windows.Forms.GroupBox>özelliğininve denetimin özelliğinintoplamıdır.<xref:System.Windows.Forms.Control.Padding%2A>

## <a name="size-controls-automatically"></a>Denetimleri otomatik olarak boyutlandır

Bazı uygulamalarda, tasarım zamanında olduğu gibi bir denetimin boyutu çalışma zamanında aynı olmayacaktır. Örneğin, bir <xref:System.Windows.Forms.Button> denetimin metni bir veritabanından alınmış olabilir ve uzunluğu önceden bilinmiyor demektir.

<xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği olarak`true`ayarlandığında, denetim kendisini içeriğine göre boyutlandıracaktır. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize özelliğini kullanarak formunuzdaki denetimleri düzenleme

1. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. Denetimin özelliğinin değerini true olarak değiştirin. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A>

3. Denetimin özelliğini bu düğme için, **Text özelliği için uzun bir dizeye sahip**olacak şekilde değiştirin. <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button>

   Değişikliği kaydettiğinizde <xref:System.Windows.Forms.Button> denetim, kendisini yeni metne sığacak şekilde yeniden boyutlandırır.

4. <xref:System.Windows.Forms.Button> **Araç kutusundan** başka bir denetimi formunuza sürükleyin.

5. Denetimin özelliğini "**Bu düğme metin özelliği için uzun bir dizeye sahip**" olarak değiştirin. <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button>

   Değişikliği kaydettiğinizde, <xref:System.Windows.Forms.Button> denetim kendisini yeniden boyutlandıramaz ve metin denetimin sağ kenarıyla kırpılır.

6. <xref:System.Windows.Forms.Control.Padding%2A> **Özellikler penceresinde** girişi genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **5**olarak ayarlayarak özelliğideğiştirin.<xref:System.Windows.Forms.Control.Padding%2A>

   Denetimin iç tarafındaki metin dört tarafa de kırpılır.

7. Denetimin özelliğini true olarak değiştirin. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A>

   Denetim <xref:System.Windows.Forms.Button> , tüm dizeyi kapsayacak şekilde kendini yeniden boyutlandırır. Ayrıca, metnin etrafına doldurma eklenmiştir ve bu da <xref:System.Windows.Forms.Button> denetimin dört yönde genişlemesine neden olur.

8. <xref:System.Windows.Forms.Button> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin. Formun sağ alt köşesinin yanına konumlandırın.

9. Denetimin özelliğinin değerini true olarak değiştirin. <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.AutoSize%2A>

10. Denetimin özelliğini ,<xref:System.Windows.Forms.AnchorStyles.Right>olarak ayarlayın. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.AnchorStyles.Bottom>

11. Denetimin özelliğini "**Bu düğme metin özelliği için uzun bir dizeye sahip**" olarak değiştirin. <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button>

   Değişikliği kaydettiğinizde, <xref:System.Windows.Forms.Button> denetim kendisini sola doğru yeniden boyutlandırır. Genel olarak, otomatik boyutlandırma, bir denetimin boyutunu, <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarına karşılık gelen yönde arttıracaktır.

## <a name="autosize-and-autosizemode-properties"></a>AutoSize ve otomatik SizeMode özellikleri

 Bazı denetimler, bir `AutoSizeMode` denetimin otomatik boyutlandırma davranışı üzerinde size daha ayrıntılı denetim sağlayan özelliğini destekler.

### <a name="use-the-autosizemode-property"></a>Oto SizeMode özelliğini kullanın

1. <xref:System.Windows.Forms.Panel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. Denetimin özelliğinin değerini true olarak ayarlayın. <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Control.AutoSize%2A>

3. Bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan denetime sürükleyin** <xref:System.Windows.Forms.Panel> .

4. <xref:System.Windows.Forms.Button> Denetimi <xref:System.Windows.Forms.Panel> denetimin sağ alt köşesine yakın yere yerleştirin.

5. <xref:System.Windows.Forms.Panel> Denetimi seçin ve sağ alt boyutlandırma tutamacını alın. <xref:System.Windows.Forms.Panel> Denetimi daha büyük ve daha küçük olacak şekilde yeniden boyutlandırın.

   > [!NOTE]
   > <xref:System.Windows.Forms.Panel> Denetimi serbestçe yeniden boyutlandırabilirsiniz, ancak <xref:System.Windows.Forms.Button> denetimin sağ alt köşesinin konumundan daha küçük boyutta olamaz. Bu davranış, `AutoSizeMode` özelliğinin <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>varsayılan değeri tarafından belirtilir.

6. <xref:System.Windows.Forms.Panel> Denetimin özelliğinin değerini olarak<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>ayarlayın. `AutoSizeMode`

   Denetim, <xref:System.Windows.Forms.Button> denetimin çevrelemek için kendisini boyutlandırır. <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Panel> Denetimi yeniden boyutlandıramazsınız.

7. <xref:System.Windows.Forms.Button> Denetimi <xref:System.Windows.Forms.Panel> denetimin sol üst köşesine doğru sürükleyin.

   Denetim, <xref:System.Windows.Forms.Button> denetimin yeni konumuna yeniden boyutlandırılır. <xref:System.Windows.Forms.Panel>

## <a name="next-steps"></a>Sonraki adımlar

Windows Forms uygulamalarınızda denetimleri düzenlemek için birçok farklı düzen özelliği vardır. Deneyebileceğiniz bazı birleşimler aşağıda verilmiştir:

- Bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi kullanarak form oluşturun. Ayrıntılar için bkz [. İzlenecek yol: TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme. Denetimin özelliğinin değerlerinin yanı sıra onun alt denetimlerindeki <xref:System.Windows.Forms.Control.Margin%2A> özelliğini değiştirmeyi deneyin. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.TableLayoutPanel>

- Bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi kullanarak aynı denemeyi deneyin. Ayrıntılar için bkz [. İzlenecek yol: FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)kullanarak Windows Forms denetimlerini düzenleme.

- Bir <xref:System.Windows.Forms.Panel> denetimde alt öğe denetimleri yerleştirmeyi deneyin. Özelliği, <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> özelliği için daha genel bir uygulamadır ve bu durum, bir <xref:System.Windows.Forms.Panel> denetime alt denetim yerleştirerek ve alt denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini olarak ayarlayarak sizin de karşılamayabilir. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Panel> Denetiminözelliğiniçeşitlideğerlereayarlayınve<xref:System.Windows.Forms.Control.Padding%2A> etkiyi göz önünde yapın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [İzlenecek yol: TableLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Anlık görüntü çizgilerini kullanarak Windows Forms denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
