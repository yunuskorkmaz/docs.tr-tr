---
title: "İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ccd5379d9594ccab02b80fd5fbdba0b202e1c69
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>İzlenecek yol: Doldurma, Kenar Boşlukları ve AutoSize Özelliği ile Windows Formları Denetimlerini Düzenleme
Formunuza denetimler tam yerleşimi, pek çok uygulama yüksek önceliktir. **Windows Form Tasarımcısı** bunu gerçekleştirmek için birçok düzen araçları sağlar. En önemli üç olan <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>, ve <xref:System.Windows.Forms.Control.AutoSize%2A> tüm Windows Forms denetimlerindeki mevcut özellikleri.  
  
 <xref:System.Windows.Forms.Control.Margin%2A> Özelliği tutar diğer denetimin Kenarlıklar belirtilen uzaklıkta denetimleri denetimi boşluk tanımlar.  
  
 <xref:System.Windows.Forms.Control.Padding%2A> Özelliği denetimin içeriğini tutan bir denetim iç kısmında yer tanımlar (örneğin, değeri kendi <xref:System.Windows.Forms.Control.Text%2A> özelliği) denetimin Kenarlıklar belirtilen uzaklıkta.  
  
 Aşağıdaki çizimde gösterildiği <xref:System.Windows.Forms.Control.Padding%2A> ve <xref:System.Windows.Forms.Control.Margin%2A> denetim özellikleri.  
  
 ![Doldurma ve kenar boşlukları Windows Forms denetimleri](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Özelliği otomatik olarak kendisini içeriğine boyut için bir denetim söyler. Özgün değerinden küçük olması kendisine boyutlandırılmayacağını <xref:System.Windows.Forms.Control.Size%2A> özelliği ve bu değeri için hesap, <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma  
  
-   Denetimler için kenar boşluklarını ayarlama  
  
-   Doldurma, denetimleri için ayarlama  
  
-   Denetimleri otomatik boyutlandırma  
  
 İşiniz bittiğinde, bu önemli yerleşim özellikleri tarafından oynadığı rol anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Oluşturma ve Windows Forms uygulaması projeleri, Visual Studio yüklü olduğu bilgisayarda çalıştırmak için yeterli izinleri yok.  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Oluşturma bir **Windows uygulaması** adlı proje `LayoutExample`. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Formda seçin **Windows Form Tasarımcısı**.  
  
## <a name="setting-margins-for-your-controls"></a>Denetimler için kenar boşluklarını ayarlama  
 Kullanarak, denetimleri varsayılan uzaklığı ayarlayabilirsiniz <xref:System.Windows.Forms.Control.Margin%2A> özelliği. Bir denetim taşıdığınızda, başka bir denetim için yeterli kapatın, iki denetim kenar boşluklarını gösteren bir snapline görürsünüz. Taşıdığınız denetim kenar boşluklarını tarafından tanımlanan mesafeye ayrıca ek.  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>Margin özelliği kullanarak, form üzerinde denetimleri düzenlemek için  
  
1.  İki <xref:System.Windows.Forms.Button> gelen denetimleri **araç** formunuza.  
  
2.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> denetler ve bunu diğer yakın, neredeyse dokunmak kadar.  
  
     Bunlar arasında görünür snapline inceleyin. Bu uzaklık iki denetimleri toplamıdır <xref:System.Windows.Forms.Control.Margin%2A> değerleri. Taşıdığınız denetim bu uzaklık tutturur. Ayrıntılar için bkz [izlenecek yol: Windows Forms kullanarak dayama çizgileri düzenleme denetimlerinde](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
3.  Değişiklik <xref:System.Windows.Forms.Control.Margin%2A> özelliği genişleterek denetimlerden birinin <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 20 özelliği.  
  
4.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> denetler ve diğer yakın taşıyın.  
  
     Snapline kenar boşluğu değerlerin toplamını uzun ve denetim büyük bir uzaklık diğer denetimden tutturur tanımlama.  
  
5.  Değişiklik <xref:System.Windows.Forms.Control.Margin%2A> genişleterek seçili denetiminin özelliğini <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.Top%2A> 5 özelliği.  
  
6.  Seçili denetimi diğer denetim altına taşıyın ve snapline kısa olup olmadığına bakın. Seçili denetimi diğer denetiminin sola taşı ve snapline 4. adımda gözlenen değer korur gözlemleyin.  
  
7.  Her yönlerinin ayarlayabilirsiniz <xref:System.Windows.Forms.Control.Margin%2A> özelliği, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, farklı değerler veya bunları tüm ile aynı değere ayarlayabilirsiniz <xref:System.Windows.Forms.Padding.All%2A> özelliği.  
  
## <a name="setting-padding-for-your-controls"></a>Doldurma, denetimleri için ayarlama  
 Uygulamanız için gerekli hassas Düzen elde etmek için denetimlerinizi genellikle alt denetimleri içerir. Üst denetimin kenarlığının alt denetimin kenarlığının yakınlığını belirtmek istediğinizde, üst denetimin kullanmak <xref:System.Windows.Forms.Control.Padding%2A> özelliği alt denetimin birlikte <xref:System.Windows.Forms.Control.Margin%2A> özelliği. <xref:System.Windows.Forms.Control.Padding%2A> Özelliği denetim içeriğinin yakınlık denetlemek için de kullanılır (örneğin, bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliği) kenarlıkları için.  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>Doldurmayı kullanarak, form üzerinde denetimleri düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
2.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.  
  
3.  Değişiklik <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 5 özelliği.  
  
     Yeni doldurma yer sağlamak üzere Denetim genişletir.  
  
4.  Sürükleme bir <xref:System.Windows.Forms.GroupBox> gelen denetim **araç** formunuza. Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.GroupBox> denetim. Konum <xref:System.Windows.Forms.Button> ile sağ alt köşesindeki temizleme olacak şekilde kontrol <xref:System.Windows.Forms.GroupBox> denetim.  
  
     Olarak görünür dayama çizgileri gözlemlemek <xref:System.Windows.Forms.Button> denetim yaklaşıyor alt ve sağ kenarlıklarını <xref:System.Windows.Forms.GroupBox> denetim. Bu dayama çizgileri karşılık <xref:System.Windows.Forms.Control.Margin%2A> özelliği <xref:System.Windows.Forms.Button>.  
  
5.  Değişiklik <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 20 özelliği.  
  
6.  Seçin <xref:System.Windows.Forms.Button> denetimine <xref:System.Windows.Forms.GroupBox> denetlemek ve merkezini doğru taşıma <xref:System.Windows.Forms.GroupBox>.  
  
     Dayama çizgileri büyük bir uzaklık kenarlıklarını görünür <xref:System.Windows.Forms.GroupBox> denetim. Bu uzaklık toplamıdır <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
## <a name="automatically-sizing-your-controls"></a>Denetimleri otomatik boyutlandırma  
 Tasarım zamanında olduğu gibi bazı uygulamalarda, denetimin boyutunu aynı çalışma zamanında olacaktır değil. Metnin bir <xref:System.Windows.Forms.Button> denetim, örneğin, alınması veritabanından ve uzunluğu önceden bilinmeyen.  
  
 Zaman <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ayarlanmış `true`, denetimi kendisini içeriğine göre boyutlanır. Daha fazla bilgi için bkz: [AutoSize özelliğine genel bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>AutoSize özelliği kullanarak, form üzerinde denetimleri düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
2.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.  
  
3.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine "**uzun bir dize Text özelliğini için bu düğmeye sahip**."  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetim kendisini yeni metnin sığması için yeniden boyutlandırır.  
  
4.  Başka bir sürükleyin <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
5.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine "**bu düğme Text özelliğini için uzun bir dize içeriyor.**"  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetimi değil yeniden boyutlandırma kendisi ve metnin sağ köşesine denetimi tarafından kırpılır.  
  
6.  Değişiklik <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 5 özelliği.  
  
     Denetimin iç metinde tüm dört tarafta kırpılır.  
  
7.  Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.  
  
     <xref:System.Windows.Forms.Button> Denetim kendisini tüm dizeyi kapsayacak şekilde yeniden boyutlandırır. Ayrıca, bir metin doldurma eklendi neden <xref:System.Windows.Forms.Button> tüm dört yönde genişletmek için denetim.  
  
8.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza. Formun sağ alt köşedeki getirin.  
  
9. Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.  
  
10. Ayarlama <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğine <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.  
  
11. Değişiklik <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine "**bu düğme Text özelliğini için uzun bir dize içeriyor.**"  
  
     Değişiklik yaparsanız <xref:System.Windows.Forms.Button> denetim yeniden boyutlandırır sola doğru kendisi. Genel olarak, otomatik boyutlandırma ters yönde bir denetim boyutunu artıracaktır kendi <xref:System.Windows.Forms.Control.Anchor%2A> özellik ayarı.  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize ve AutoSizeMode özellikleri  
 Bazı denetimler Destek `AutoSizeMode` özelliği bir denetimin otomatik boyutlandırma davranışı üzerinde daha ayrıntılı denetim sağlar.  
  
#### <a name="to-use-the-autosizemode-property"></a>AutoSizeMode özelliği kullanmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Panel> gelen denetim **araç** formunuza.  
  
2.  Değerini <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.Panel> denetim.  
  
4.  Yer <xref:System.Windows.Forms.Button> sağ alt köşesindeki yakın denetim <xref:System.Windows.Forms.Panel> denetim.  
  
5.  Seçin <xref:System.Windows.Forms.Panel> denetlemek ve sağ alt köşedeki boyutlandırma tutamacını yakalayın. Yeniden boyutlandırma <xref:System.Windows.Forms.Panel> denetim büyük ve küçük olmalıdır.  
  
    > [!NOTE]
    >  Ücretsiz olarak boyutlandırabilirsiniz <xref:System.Windows.Forms.Panel> denetimi, ancak olamaz boyut, küçüktür konumunu <xref:System.Windows.Forms.Button> denetimin sağ alt köşedeki. Bu davranış varsayılan değeri tarafından belirtilen `AutoSizeMode` olan özelliği, <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.  
  
6.  Değerini <xref:System.Windows.Forms.Panel> denetimin `AutoSizeMode` özelliğine <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.  
  
     <xref:System.Windows.Forms.Panel> Denetim kendisini çevreleyen boyutları <xref:System.Windows.Forms.Button> denetim. Yeniden boyutlandırma olamaz <xref:System.Windows.Forms.Panel> denetim.  
  
7.  Sürükleme <xref:System.Windows.Forms.Button> denetim sol üst köşesindeki doğru <xref:System.Windows.Forms.Panel> denetim.  
  
     <xref:System.Windows.Forms.Panel> Denetim göre yeniden boyutlandırır <xref:System.Windows.Forms.Button> denetimin yeni konumu.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Windows Forms uygulamalarında denetimleri düzenleme için birçok düzeni özelliği vardır. Deneyebilecekleriniz bazı birleşimleri şunlardır:  
  
-   Kullanarak bir form derleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetim. Ayrıntılar için bkz [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Değerini değiştirmeyi deneyin <xref:System.Windows.Forms.TableLayoutPanel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliği, hem de <xref:System.Windows.Forms.Control.Margin%2A> alt denetimlerinden özelliği.  
  
-   Kullanarak aynı denemeyi deneyin bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim. Ayrıntılar için bkz [izlenecek yol: Windows Forms FlowLayoutPanel kullanarak düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
-   Alt denetimler yerleştirme ile deneme bir <xref:System.Windows.Forms.Panel> denetim. <xref:System.Windows.Forms.Control.Padding%2A> Özelliği olan, daha fazla genel gerçekleştirme <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> özelliği ve karşılamak kendiniz alt denetimini koyarak kullanılabilir durumda olup olmadığını bir <xref:System.Windows.Forms.Panel> denetim ve alt denetim ayarını <xref:System.Windows.Forms.Control.Dock%2A> özelliğine<xref:System.Windows.Forms.DockStyle.Fill>. Ayarlama <xref:System.Windows.Forms.Panel> denetimin <xref:System.Windows.Forms.Control.Padding%2A> özelliğini çeşitli değerleri ve Not etkisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 [AutoSize Özelliğine Genel Bakış](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [İzlenecek yol: TableLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: FlowLayoutPanel Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
