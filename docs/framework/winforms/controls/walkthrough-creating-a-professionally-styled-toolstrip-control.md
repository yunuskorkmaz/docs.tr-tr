---
title: 'İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211764"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>İzlenecek yol: Profesyonel Stilde ToolStrip Denetimi Oluşturma

Uygulamanızın verebilirsiniz <xref:System.Windows.Forms.ToolStrip> kendi sınıfından türetilen yazarak bir profesyonel görünümünü ve davranışını denetleyen <xref:System.Windows.Forms.ToolStripProfessionalRenderer> türü.

Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStrip> benzeyen bileşik denetim oluşturmak için denetimleri **Gezinti bölmesinde** Microsoft Outlook® tarafından sağlanan. Aşağıdaki görevler bu kılavuzda gösterilen:

- Bir Windows Denetim Kitaplığı projesi oluşturma.

- StackView denetimi tasarlama.

- Özel oluşturucu oluşturma.

İşlemi tamamladığınızda, profesyonel bir Microsoft Office® XP denetiminin görünümünü ile bir yeniden kullanılabilir bir özel istemci denetime sahip olur.

Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Profesyonel stilde ToolStrip denetimi oluşturma](how-to-create-a-professionally-styled-toolstrip-control.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio gerekir.

## <a name="create-the-control-library-project"></a>Denetim Kitaplığı projesi oluşturun

1. Visual Studio'da adlı yeni bir Windows Denetim Kitaplığı projesi oluşturma `StackViewLibrary`.

2. İçinde **Çözüm Gezgini**, istediğiniz dilde bağlı olarak "UserControl1.cs" veya "UserControl1.vb" adlı kaynak dosyası silerek projenin varsayılan denetimini silin.

     Daha fazla bilgi için [nasıl yapılır: , Silme, kaldırmak ve öğeleri hariç](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).

3. Yeni bir <xref:System.Windows.Forms.UserControl> öğesinin **StackViewLibrary** proje. Yeni kaynak dosyanın temel adı verin `StackView`.

## <a name="design-the-stackview-control"></a>Tasarım StackView denetimi

`StackView` Denetimdir: bir alt öğesi ile bileşik denetim <xref:System.Windows.Forms.ToolStrip> denetimi. Bileşik denetimler hakkında daha fazla bilgi için bkz: [özel denetim çeşitleri](varieties-of-custom-controls.md).

1. Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.ToolStrip> denetimi tasarım yüzeyine bırakın.

2. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStrip> denetimin özellikleri aşağıdaki tabloya göre.

    |Özellik|Değer|
    |--------------|-----------|
    |Ad|`stackStrip`|
    |CanOverflow|`false`|
    |Dock|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |Yazı tipi|`Tahoma, 10pt, style=Bold`|
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |Doldurma|`0, 7, 0, 0`|
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. Windows Form Tasarımcısı'nda tıklatın <xref:System.Windows.Forms.ToolStrip> denetimin **Ekle** düğmesine tıklayın ve Ekle bir <xref:System.Windows.Forms.ToolStripButton> için `stackStrip` denetimi.

4. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolStripButton> denetimin özellikleri aşağıdaki tabloya göre.

    |Özellik|Değer|
    |--------------|-----------|
    |Ad|`mailStackButton`|
    |CheckOnClick|true|
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |ImageTransparentColor|`238, 238, 238`|
    |Kenar boşluğu|`0, 0, 0, 0`|
    |Doldurma|`3, 3, 3, 3`|
    |Metin|**posta**|
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. Daha fazla üç için yineleme adım 7 <xref:System.Windows.Forms.ToolStripButton> kontrol eder.

     Denetimlere `calendarStackButton`, `contactsStackButton`, ve `tasksStackButton`. Değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Takvim**, **kişiler**, ve **görevleri**sırasıyla.

## <a name="handle-events"></a>Olayları işleme

İki olay yapmak önemli `StackView` denetimi doğru şekilde davranır. Tanıtıcı <xref:System.Windows.Forms.UserControl.Load> denetim doğru konuma olay. Tanıtıcı <xref:System.Windows.Forms.ToolStripItem.Click> her olay <xref:System.Windows.Forms.ToolStripButton> vermek `StackView` denetim durumu davranışını benzer <xref:System.Windows.Forms.RadioButton> denetimi.

1. Windows Form Tasarımcısı'nda seçin `StackView` denetimi.

2. İçinde **özellikleri** penceresinde tıklayın **olayları**.

3. Oluşturulacak yükleme olayı çift `StackView_Load` olay işleyicisi.

4. İçinde `StackView_Load` olay işleyicisine aşağıdaki kodu kopyalayıp yapıştırın.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. Windows Form Tasarımcısı'nda seçin `mailStackButton` denetimi.

6. İçinde **özellikleri** penceresinde tıklayın **olayları**.

7. Tıklama olayı çift tıklatın.

     Windows Form Tasarımcısı oluşturur `mailStackButton_Click` olay işleyicisi.

8. Yeniden adlandırma `mailStackButton_Click` olay işleyicisine `stackButton_Click`.

     Daha fazla bilgi için [bir kod sembol yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).

9. Aşağıdaki kodu ekleyin `stackButton_Click` olay işleyicisi.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. Windows Form Tasarımcısı'nda seçin `calendarStackButton` denetimi.

11. İçinde **özellikleri** penceresinde ayarlanmış Click olayı `stackButton_Click` olay işleyicisi.

12. 10 ve 11. adımları yineleyin `contactsStackButton` ve `tasksStackButton` kontrol eder.

## <a name="define-icons"></a>Simgeleri tanımlayın

Her `StackView` düğmeye sahip bir ilişkili simge. Kolaylık olması için simgeleri Base64 ile kodlanmış bir dize olarak, önce seri durumdan temsil edilen bir <xref:System.Drawing.Bitmap> ondan oluşturulur. Bir üretim ortamında bir kaynak olarak bit eşlem verileri depolamak ve simgelerini Windows Form Tasarımcısı'nda görünür. Daha fazla bilgi için [nasıl yapılır: Windows formlarına arka plan görüntüleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).

1. Kod Düzenleyicisi'nde aşağıdaki kodu ekleyin `StackView` sınıf tanımını. Bu kod için bit eşlemler başlatır <xref:System.Windows.Forms.ToolStripButton> simgeler.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. Bir çağrı ekleyin `InitializeImages` yönteminde `StackView` sınıf oluşturucusu.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a>Uygulama özel Oluşturucu

Özelleştirebileceğiniz öğelerin çoğunu `StackView` my türetildiği bir sınıf uygulama Denetim <xref:System.Windows.Forms.ToolStripRenderer> sınıfı. Bu yordamda, uygulamanız bir <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tutamacı özelleştirir ve gradyan arka planlar için çizer sınıfı <xref:System.Windows.Forms.ToolStripButton> kontrol eder.

1. Aşağıdaki kodu ekleyin `StackView` denetim tanımı.

     Bu tanımı, `StackRenderer` sınıfı, hangi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, ve <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> özel görünüm oluşturmak için yöntemleri.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. İçinde `StackView` denetimin Oluşturucu, yeni bir örneğini oluşturmak `StackRenderer` sınıfı ve bu örneğe atama `stackStrip` denetimin <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özelliği.

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a>Test StackView denetimi

`StackView` Denetim türetilir <xref:System.Windows.Forms.UserControl> sınıfı. Bu nedenle, Denetim ile test edebilirsiniz **UserControl Test kapsayıcısı**. Daha fazla bilgi için [nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

1. Tuşuna **F5** projeyi oluşturmak ve başlatmak için **UserControl Test kapsayıcısı**.

2. Düğmelerinin üzerinde işaretçiyi `StackView` denetlemek ve ardından seçili durumuna görünümünü görmek için bir düğmesine tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, profesyonel bir Office XP denetiminin görünümünü ile yeniden kullanılabilir bir özel istemci denetimi oluşturdunuz. Kullanabileceğiniz <xref:System.Windows.Forms.ToolStrip> birçok başka amaçlarla denetimlerin ailesi:

- Sahip, denetimler için kısayol menüleri oluşturma <xref:System.Windows.Forms.ContextMenuStrip>. Daha fazla bilgi için [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).

- Bir formu otomatik olarak doldurulan bir standart menü ile oluşturun. Daha fazla bilgi için [izlenecek yol: Bir forma standart menü öğeleri sağlama](walkthrough-providing-standard-menu-items-to-a-form.md).

- Yerleştirme ile birden çok belge arabirimi (MDI) form oluşturma <xref:System.Windows.Forms.ToolStrip> kontrol eder. Daha fazla bilgi için [nasıl yapılır: Menü birleştirme ve ToolStrip denetimleri içeren MDI formu oluşturma](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
- [Nasıl yapılır: Bir forma standart menü öğeleri sağlama](how-to-provide-standard-menu-items-to-a-form.md)
