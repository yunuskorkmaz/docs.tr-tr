---
title: "İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma"
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: b606de4b7cf4648fdc7ada3c1f6faec81342d02c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320645"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma
Visual Basic ile aracılığıyla güçlü özel denetimler oluşturabilirsiniz *devralma*. Devralma üzerinden tüm standart Windows Forms denetimleri devralınan işlevlerini korur, ancak özel işlevler de dahil denetimleri oluşturabilirsiniz. Bu izlenecek yolda, adlı basit bir devralınan denetim oluşturacaksınız `ValueButton`. Bu düğme, standart Windows Forms işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı bir özel özellik açığa çıkarır `ButtonValue`.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2. Seçin **Windows Forms Denetim Kitaplığı** proje şablonu Visual Basic projeleri ve türü listesinden `ValueButtonLib` içinde **adı** kutusu.  
  
     Proje adı `ValueButtonLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır. Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`. Daha fazla bilgi için [Visual Basic'de ad alanları](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3. İçinde **Çözüm Gezgini**, sağ **UserControl1.vb**, ardından **Yeniden Adlandır** kısayol menüsünden. İçin dosya adını değiştirerek `ValueButton.vb`. Tıklayın **Evet** yaptığınız 'UserControl1' kod öğesi için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda düğmesi.  
  
4. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.  
  
5. Açık **ValueButton.vb** kod tasarımcı tarafından oluşturulan dosya görüntülenecek düğümü **ValueButton.Designer.vb**. Bu dosyayı açmak **Kod Düzenleyicisi**.  
  
6. Bulun `Class` deyimi `Partial Public Class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>. Böylece tüm işlevlerini devralmak devralınan denetim <xref:System.Windows.Forms.Button> denetimi.  
  
7. Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satırı <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği. Bu özellik yok <xref:System.Windows.Forms.Button> denetimi.  
  
8. Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
     Bir görsel tasarımcı artık kullanılabilir olduğuna dikkat edin. Çünkü <xref:System.Windows.Forms.Button> netimi kendi boyama, Tasarımcı içinde görünümünü değiştirilemedi. Görsel gösterimine tam olarak aynı sınıfından devralan sınıf olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değiştirilmediği sürece.  
  
> [!NOTE]
>  Tasarım yüzeyine UI öğesi içermeyen olan bileşenleri eklemeye devam edebilirsiniz.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Devralınan denetiminize özellik ekleme  
 Bir olası devralınan Windows Forms denetimleri, standart Windows Forms denetimlerine görünümünü ve davranışını (Görünüm) içinde aynıdır, ancak özel özellikler kullanıma denetimleri oluşturulmasını kullanılır. Bu bölümde, adlı bir özellik ekleyeceksiniz `ButtonValue` denetiminiz için.  
  
#### <a name="to-add-the-value-property"></a>Value özelliği eklemek için  
  
1. İçinde **Çözüm Gezgini**, sağ **ValueButton.vb**ve ardından **kodu görüntüle** kısayol menüsünden.  
  
2. Bulun `Public Class ValueButton` deyimi. Hemen bu bildirimi, aşağıdaki kodu yazın:  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır. `Get` Deyimi ayarlar özel bir değişkende depolanan değere döndürülen değer `varValue`ve `Set` deyimi kullanarak özel bir değişken değerini ayarlar `Value` anahtar sözcüğü.  
  
3. Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-your-control"></a>Denetiminiz test etme  
 Denetimler, tek başına projeleri değildir; Bunlar, bir kapsayıcıda barındırılan gerekir. Denetiminiz test etmek için bir test projesi için bunu çalıştırmak için sağlamanız gerekir. Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir. Bu bölümde, denetiminizi oluşturup bir Windows formunda test.  
  
#### <a name="to-build-your-control"></a>Denetim oluşturmak için  
  
1. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Derleme, derleyici hata veya uyarılar ile başarılı olmalıdır.  
  
#### <a name="to-create-a-test-project"></a>Bir test projesi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2. Visual Basic projeleri düğümünü seçin ve tıklayın **Windows Forms uygulaması**.  
  
3. İçinde **adı** kutusuna `Test`.  
  
4. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.  
  
5. İçinde **Çözüm Gezgini**, sağ **başvuruları** ardından düğümü test projeniz için **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.  
  
6. Tıklayın **projeleri** sekmesi.  
  
7. Etiketli sekmesini **projeleri**. `ValueButtonLib` Projesi altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
8. İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Forma denetim ekleme  
  
1. İçinde **Çözüm Gezgini**, sağ **Form1.vb** ve **Görünüm Tasarımcısı** kısayol menüsünden.  
  
2. İçinde **araç kutusu**, tıklayın **ValueButtonLib bileşenleri**. Çift **ValueButton**.  
  
     A **ValueButton** formda görünür.  
  
3. Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.  
  
4. İçinde **özellikleri** penceresinde, bu denetimin özelliklerini inceleyin. Ek bir özellik olduğundan dışında standart bir düğme tarafından kullanıma sunulan özellikleri aynı olduklarını unutmayın `ButtonValue`.  
  
5. Ayarlama `ButtonValue` özelliğini `5`.  
  
6. Üzerinde **tüm Windows Formları** sekmesinde **araç kutusu**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> form denetimi.  
  
7. Etiket biçiminin merkezine taşımanızı.  
  
8. Çift `ValueButton1`.  
  
     **Kod Düzenleyicisi** açılır `ValueButton1_Click` olay.  
  
9. Aşağıdaki kod satırını yazın.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. İçinde **Çözüm Gezgini**, sağ **Test**ve **başlangıç projesi olarak ayarla** kısayol menüsünden.  
  
11. Gelen **hata ayıklama** menüsünde **hata ayıklamayı Başlat**.  
  
     `Form1` görünür.  
  
12. Tıklatın `Valuebutton1`.  
  
     '5' sayısal görüntülenen `Label1`elde, `ButtonValue` devralınan denetim özelliği için geçirilmiş `Label1` aracılığıyla `ValueButton1_Click` yöntemi. Bu nedenle, `ValueButton` denetimi, standart Windows Forms düğmesini tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Visual Basic ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)
- [Devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
