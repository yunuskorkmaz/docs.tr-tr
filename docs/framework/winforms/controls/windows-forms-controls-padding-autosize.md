---
title: Denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca7942c04434592f2541252c47ac3dd17e03dbac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742378"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>İzlenecek yol: doldurma, kenar boşlukları ve AutoSize özelliği ile denetimleri düzenleme

Denetimlerin formunuza kesin olarak yerleştirilmesi birçok uygulama için yüksek önceliktir. Visual Studio 'daki **Windows Form Tasarımcısı** , bunu gerçekleştirmek için size çok sayıda düzen aracı sağlar. En önemlileri, tüm Windows Forms Denetimlerinde bulunan <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>ve <xref:System.Windows.Forms.Control.AutoSize%2A> özelliklerdir.

<xref:System.Windows.Forms.Control.Margin%2A> özelliği, denetimin kenarlıklarından belirli bir uzaklıkta bulunan diğer denetimleri tutan denetimin etrafındaki boşluğu tanımlar.

<xref:System.Windows.Forms.Control.Padding%2A> özelliği, denetimin içeriklerini (örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliğinin değeri) denetimin kenarlıklarından belirtilen mesafeden tutan bir denetimin iç kısmında yer alan alanı tanımlar.

Aşağıdaki çizimde bir denetimdeki <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> özellikleri gösterilmektedir.

![Windows Forms denetimleri için doldurma ve kenar boşluğu](./media/vs-winformpadmargin.gif)

<xref:System.Windows.Forms.Control.AutoSize%2A> özelliği, bir denetime kendi içeriğini otomatik olarak boyutunu söylemektedir. Kendisini özgün <xref:System.Windows.Forms.Control.Size%2A> özelliğinin değerinden küçük olacak şekilde yeniden boyutlandıramaz ve <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin değeri için hesaba sahip olur.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'da `LayoutExample`adlı bir **Windows uygulaması** projesi oluşturun.

2. **Windows Form Tasarımcısı**formunu seçin.

## <a name="set-margins-for-controls"></a>Denetimler için kenar boşluklarını ayarlama

<xref:System.Windows.Forms.Control.Margin%2A> özelliğini kullanarak, denetimleriniz arasındaki varsayılan mesafeyi ayarlayabilirsiniz. Bir denetimi başka bir denetime kadar yakından taşıdığınızda, iki denetim için kenar boşluklarını gösteren bir anlık görüntü satırı görürsünüz. Taşıdığınız denetim, kenar boşlukları tarafından tanımlanan uzaklıktan de yaslıolur.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Kenar boşluğu özelliğini kullanarak formunuzdaki denetimleri düzenleme

1. **Araç kutusundan** iki <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> denetimlerinden birini seçin ve neredeyse dokunana kadar bir sonrakine geçin.

   Aralarında görüntülenen anlık görüntü çizgisini gözlemleyin. Bu uzaklık, iki denetimin <xref:System.Windows.Forms.Control.Margin%2A> değerlerinin toplamıdır. Taşıdığınız denetim bu uzaklığa yapışır. Ayrıntılar için bkz. [Izlenecek yol: Windows Forms denetimleri yerleştirme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Bir denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğini, **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Margin%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **20**olarak ayarlayarak değiştirin.

4. <xref:System.Windows.Forms.Button> denetimlerinden birini seçin ve diğerine yakın taşıyın.

   Kenar boşluğu değerlerinin toplamını tanımlayan anlık görüntü satırı daha uzundur ve denetimin diğer denetimden daha fazla mesafeye yaslanır.

5. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Margin%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.Top%2A> özelliğini **5**olarak ayarlayarak seçili denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliğini değiştirin.

6. Seçili denetimi diğer denetimin altına taşıyın ve Snapın çizgisinin daha kısa olduğunu gözlemleyin. Seçili denetimi diğer denetimin soluna taşıyın ve Snapın değerinin 4. adımda gözlenen değeri koruduğunu gözlemleyin.

7. <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin her birini, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>farklı değerlere ayarlayabilir veya tümünü, <xref:System.Windows.Forms.Padding.All%2A> özelliğiyle aynı değere ayarlayabilirsiniz.

## <a name="set-padding-for-controls"></a>Denetimler için doldurma ayarla

Uygulamanız için gereken kesin düzeni elde etmek için, denetimleriniz genellikle alt denetimler içerir. Alt denetimin kenarlığının üst denetimin kenarlığına yakınlığını belirtmek istediğinizde, üst denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini alt denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği ile birlikte kullanın. <xref:System.Windows.Forms.Control.Padding%2A> özelliği, bir denetimin içeriğinin (örneğin, bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliği) kenarlıklarını denetlemek için de kullanılır.

### <a name="arrange-controls-on-your-form-using-padding"></a>Doldurma kullanarak formunuzdaki denetimleri düzenleme

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini **true**olarak değiştirin.

3. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Padding%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **5**olarak ayarlayarak <xref:System.Windows.Forms.Control.Padding%2A> özelliğini değiştirin.

   Denetim, yeni doldurma için yer sağlamak üzere genişler.

4. **Araç kutusundan** bir <xref:System.Windows.Forms.GroupBox> denetimini formunuza sürükleyin. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.GroupBox> denetimine sürükleyin. <xref:System.Windows.Forms.Button> denetimini, <xref:System.Windows.Forms.GroupBox> denetiminin sağ alt köşesine doğru konumlandırın.

   <xref:System.Windows.Forms.Button> denetim, <xref:System.Windows.Forms.GroupBox> denetiminin alt ve sağ kenarlıklarına yaklaşırsa, görünen ek çizgi çizgilerini gözlemleyin. Bu ek çizgi, <xref:System.Windows.Forms.Button><xref:System.Windows.Forms.Control.Margin%2A> özelliğine karşılık gelir.

5. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Padding%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **20**olarak ayarlayarak <xref:System.Windows.Forms.GroupBox> denetiminin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini değiştirin.

6. <xref:System.Windows.Forms.GroupBox> denetimindeki <xref:System.Windows.Forms.Button> denetimini seçin ve <xref:System.Windows.Forms.GroupBox>merkezine doğru taşıyın.

   Anlık görüntü çizgileri, <xref:System.Windows.Forms.GroupBox> denetiminin kenarlıklarından daha fazla mesafede görüntülenir. Bu uzaklık <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin ve <xref:System.Windows.Forms.GroupBox> denetiminin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin toplamıdır.

## <a name="size-controls-automatically"></a>Denetimleri otomatik olarak boyutlandır

Bazı uygulamalarda, tasarım zamanında olduğu gibi bir denetimin boyutu çalışma zamanında aynı olmayacaktır. Örneğin, bir <xref:System.Windows.Forms.Button> denetimin metni bir veritabanından alınmış olabilir ve uzunluğu önceden bilinmiyor demektir.

<xref:System.Windows.Forms.Control.AutoSize%2A> özelliği `true`olarak ayarlandığında, denetim kendisini içeriğine göre boyutlandıracaktır. Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize özelliğini kullanarak formunuzdaki denetimleri düzenleme

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini **true**olarak değiştirin.

3. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Bu düğmenin metin özelliği için uzun bir dizeye sahip**olacak şekilde değiştirin.

   Değişikliği kaydettiğinizde, <xref:System.Windows.Forms.Button> denetimi kendisini yeni metne sığacak şekilde yeniden boyutlandırır.

4. **Araç kutusundan** başka bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin.

5. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini "**Bu düğme metin özelliği için uzun bir dizeye sahip**" olarak değiştirin.

   Değişikliği kaydettiğinizde, <xref:System.Windows.Forms.Button> denetimi kendisini yeniden boyutlandıramaz ve metin denetimin sağ kenarıyla kırpılır.

6. **Özellikler** penceresinde <xref:System.Windows.Forms.Control.Padding%2A> girdisini genişleterek ve <xref:System.Windows.Forms.Padding.All%2A> özelliğini **5**olarak ayarlayarak <xref:System.Windows.Forms.Control.Padding%2A> özelliğini değiştirin.

   Denetimin iç tarafındaki metin dört tarafa de kırpılır.

7. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini **true**olarak değiştirin.

   <xref:System.Windows.Forms.Button> denetimi kendinden tüm dizeyi kapsayacak şekilde yeniden boyutlandırır. Ayrıca, metnin etrafına doldurma eklenmiştir ve bu da <xref:System.Windows.Forms.Button> denetiminin dört yönde genişlemesine neden olur.

8. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini formunuza sürükleyin. Formun sağ alt köşesinin yanına konumlandırın.

9. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini **true**olarak değiştirin.

10. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>olarak ayarlayın.

11. <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini "**Bu düğme metin özelliği için uzun bir dizeye sahip**" olarak değiştirin.

   Değişikliği kaydettiğinizde, <xref:System.Windows.Forms.Button> denetimi kendisini sola doğru bir şekilde yeniden boyutlandırır. Genel olarak, otomatik boyutlandırma, <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarına karşı yönde bir denetimin boyutunu artırır.

## <a name="autosize-and-autosizemode-properties"></a>AutoSize ve otomatik SizeMode özellikleri

 Bazı denetimler, bir denetimin otomatik boyutlandırma davranışı üzerinde size daha ayrıntılı denetim sağlayan `AutoSizeMode` özelliğini destekler.

### <a name="use-the-autosizemode-property"></a>Oto SizeMode özelliğini kullanın

1. **Araç kutusundan** bir <xref:System.Windows.Forms.Panel> denetimini formunuza sürükleyin.

2. <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğinin değerini **true**olarak ayarlayın.

3. **Araç kutusundan** bir <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.Panel> denetimine sürükleyin.

4. <xref:System.Windows.Forms.Button> denetimini, <xref:System.Windows.Forms.Panel> denetiminin sağ alt köşesine yakın bir yere yerleştirin.

5. <xref:System.Windows.Forms.Panel> denetimini seçin ve sağ alt boyutlandırma tutamacını alın. <xref:System.Windows.Forms.Panel> denetimini daha büyük ve daha küçük olacak şekilde yeniden boyutlandırın.

   > [!NOTE]
   > <xref:System.Windows.Forms.Panel> denetimini serbestçe yeniden boyutlandırabilirsiniz, ancak <xref:System.Windows.Forms.Button> denetiminin sağ alt köşesinin konumundan daha küçük bir boyut olamaz. Bu davranış, <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>`AutoSizeMode` özelliğinin varsayılan değeri tarafından belirtilir.

6. <xref:System.Windows.Forms.Panel> denetiminin `AutoSizeMode` özelliğinin değerini <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>olarak ayarlayın.

   <xref:System.Windows.Forms.Panel> denetim, <xref:System.Windows.Forms.Button> denetimini çevreleyecek şekilde boyutlandırır. <xref:System.Windows.Forms.Panel> denetimini yeniden boyutlandıramazsınız.

7. <xref:System.Windows.Forms.Button> denetimini <xref:System.Windows.Forms.Panel> denetiminin sol üst köşesine doğru sürükleyin.

   <xref:System.Windows.Forms.Panel> denetimi <xref:System.Windows.Forms.Button> denetiminin yeni konumuna yeniden boyutlandırır.

## <a name="next-steps"></a>Sonraki adımlar

Windows Forms uygulamalarınızda denetimleri düzenlemek için birçok farklı düzen özelliği vardır. Deneyebileceğiniz bazı birleşimler aşağıda verilmiştir:

- <xref:System.Windows.Forms.TableLayoutPanel> denetimi kullanarak form oluşturun. Ayrıntılar için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). <xref:System.Windows.Forms.TableLayoutPanel> denetiminin <xref:System.Windows.Forms.Control.Padding%2A> özelliğinin ve alt denetimlerindeki <xref:System.Windows.Forms.Control.Margin%2A> özelliğinin değerlerini değiştirmeyi deneyin.

- <xref:System.Windows.Forms.FlowLayoutPanel> denetimi kullanarak aynı denemeyi deneyin. Ayrıntılar için bkz. [Izlenecek yol: Windows Forms denetimleri bir FlowLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Bir <xref:System.Windows.Forms.Panel> denetiminde alt öğe denetimleri yerleştirmeyi deneyin. <xref:System.Windows.Forms.Control.Padding%2A> özelliği, <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> özelliğinin daha genel bir çalışmasında ve bu durum, bir <xref:System.Windows.Forms.Panel> denetimine bir alt denetim yerleştirerek ve alt denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliği <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlanarak sizin tarafınızdan karşılamayabilir. <xref:System.Windows.Forms.Panel> denetiminin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini çeşitli değerlere ayarlayın ve etkiyi göz önünde edin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize Özelliğine Genel Bakış](autosize-property-overview.md)
- [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
