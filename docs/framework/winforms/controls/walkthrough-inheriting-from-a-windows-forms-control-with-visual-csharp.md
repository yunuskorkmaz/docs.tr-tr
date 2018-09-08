---
title: "İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma"
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: cad15b8fb89ec17e45b0f6cfed22f3109551fc2c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130899"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma #
İle [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], güçlü özel denetimler aracılığıyla oluşturabilirsiniz *devralma*. Devralma üzerinden tüm standart Windows Forms denetimleri devralınan işlevlerini korur, ancak özel işlevler de dahil denetimleri oluşturabilirsiniz. Bu izlenecek yolda, adlı basit bir devralınan denetim oluşturacaksınız `ValueButton`. Bu düğme, standart Windows Forms işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı bir özel özellik açığa çıkarır `ButtonValue`.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlayın ve varsayılan bileşeni doğru ad alanı içinde olmasını sağlamak için adını belirtin.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Seçin **Windows Forms Denetim Kitaplığı** proje şablonu Visual C# projeleri ve türü listesinden `ValueButtonLib` içinde **adı** kutusu.  
  
     Proje adı `ValueButtonLib`, aynı zamanda kök ad alanı için varsayılan olarak atanır. Kök ad alanı, bileşenleri derleme içindeki adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`. Daha fazla bilgi için [ad alanları](../../../csharp/programming-guide/namespaces/index.md).  
  
3.  İçinde **Çözüm Gezgini**, sağ **UserControl1.cs**, ardından **Yeniden Adlandır** kısayol menüsünden. İçin dosya adını değiştirerek `ValueButton.cs`. Tıklayın **Evet** düğmesini yaptığınız kod öğesi için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda '`UserControl1`'.  
  
4.  İçinde **Çözüm Gezgini**, sağ **ValueButton.cs** seçip **kodu görüntüle**.  
  
5.  Bulun `class` deyim satırı `public partial class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>. Böylece tüm işlevlerini devralmak devralınan denetim <xref:System.Windows.Forms.Button> denetimi.  
  
6.  İçinde **Çözüm Gezgini**açın **ValueButton.cs** kod tasarımcı tarafından oluşturulan dosya görüntülenecek düğümü **ValueButton.Designer.cs**. Bu dosyayı açmak **Kod Düzenleyicisi**.  
  
7.  Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satırı <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği. Bu özellik yok <xref:System.Windows.Forms.Button> denetimi.  
  
8.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
    > [!NOTE]
    >  Bir görsel tasarımcı artık kullanılamıyor. Çünkü <xref:System.Windows.Forms.Button> netimi kendi boyama, Tasarımcı içinde görünümünü değiştirilemedi. Görsel gösterimine tam olarak aynı sınıfından devralan sınıf olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değiştirilmediği sürece. Tasarım yüzeyine UI öğesi içermeyen olan bileşenleri eklemeye devam edebilirsiniz.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Devralınan denetiminize özellik ekleme  
 Bir olası devralınan Windows Forms denetimlerinin Görünüm ve yapısını standart Windows Forms denetimleri aynıdır, ancak özel özellikler kullanıma denetimleri oluşturulmasını kullanılır. Bu bölümde, adlı bir özellik ekleyeceksiniz `ButtonValue` denetiminiz için.  
  
#### <a name="to-add-the-value-property"></a>Value özelliği eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ValueButton.cs**ve ardından **kodu görüntüle** kısayol menüsünden.  
  
2.  Bulun `class` deyimi. Hemen sonra `{`, aşağıdaki kodu yazın:  
  
    ```csharp  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır. `get` Deyimi ayarlar özel bir değişkende depolanan değere döndürülen değer `varValue`ve `set` deyimi kullanarak özel bir değişken değerini ayarlar `value` anahtar sözcüğü.  
  
3.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-your-control"></a>Denetiminiz test etme  
 Denetimler, tek başına projeleri değildir; Bunlar, bir kapsayıcıda barındırılan gerekir. Denetiminiz test etmek için bir test projesi için bunu çalıştırmak için sağlamanız gerekir. Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir. Bu bölümde, denetiminizi oluşturup bir Windows formunda test.  
  
#### <a name="to-build-your-control"></a>Denetim oluşturmak için  
  
1.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
     Derleme, derleyici hata veya uyarılar ile başarılı olmalıdır.  
  
#### <a name="to-create-a-test-project"></a>Bir test projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Seçin **Windows** düğümü, beneath **Visual C#** düğüm seçeneğine tıklayıp **Windows Forms uygulaması**.  
  
3.  İçinde **adı** kutusuna `Test`.  
  
4.  İçinde **Çözüm Gezgini**, sağ **başvuruları** ardından düğümü test projeniz için **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.  
  
5.  Etiketli sekmesini **projeleri**. `ValueButtonLib` Projesi altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
6.  İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Forma denetim ekleme  
  
1.  İçinde **Çözüm Gezgini**, sağ **Form1.cs** ve **Görünüm Tasarımcısı** kısayol menüsünden.  
  
2.  İçinde **araç kutusu**, tıklayın **ValueButtonLib bileşenleri**. Çift **ValueButton**.  
  
     A **ValueButton** formda görünür.  
  
3.  Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.  
  
4.  İçinde **özellikleri** penceresinde, bu denetimin özelliklerini inceleyin. Ek bir özellik olduğundan dışında standart bir düğme tarafından kullanıma sunulan özellikleri aynı olduklarını unutmayın `ButtonValue`.  
  
5.  Ayarlama `ButtonValue` özelliğini `5`.  
  
6.  İçinde **tüm Windows Formları** sekmesinde **araç kutusu**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> form denetimi.  
  
7.  Etiket biçiminin merkezine taşımanızı.  
  
8.  Çift `valueButton1`.  
  
     **Kod Düzenleyicisi** açılır `valueButton1_Click` olay.  
  
9. Aşağıdaki kod satırını ekleyin.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. İçinde **Çözüm Gezgini**, sağ **Test**ve **başlangıç projesi olarak ayarla** kısayol menüsünden.  
  
11. Gelen **hata ayıklama** menüsünde **hata ayıklamayı Başlat**.  
  
     `Form1` görünür.  
  
12. Tıklatın `valueButton1`.  
  
     '5' sayısal görüntülenen `label1`elde, `ButtonValue` devralınan denetim özelliği için geçirilmiş `label1` aracılığıyla `valueButton1_Click` yöntemi. Bu nedenle, `ValueButton` denetimi, standart Windows Forms düğmesini tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bileşenler ile programlama](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Bileşen yazma izlenecek yolları](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
