---
title: "İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b165de0d18cede275dfe8405b0266c1a909ac570
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma
İle [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], güçlü özel denetimlerde oluşturabilirsiniz *devralma*. Devralma sayesinde, tüm standart Windows Forms denetimleri devralınmış işlevselliğini korur, ancak ayrıca özel işlevselliğine sahiptir denetimleri oluşturabilirsiniz. Bu kılavuzda, adlı basit bir devralınan denetim oluşturacak `ValueButton`. Bu düğme standart Windows formlarının dışında işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı özel bir özellik kullanıma `ButtonValue`.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlamak için ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adını belirtin.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Seçin **Windows Forms Denetim Kitaplığı** proje şablonu listesinden [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projeleri ve türü `ValueButtonLib` içinde **adı** kutusu.  
  
     Proje adı `ValueButtonLib`, kök ad alanı için varsayılan olarak da atanmış. Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`. Daha fazla bilgi için bkz: [Visual Basic'de ad alanları](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  İçinde **Çözüm Gezgini**, sağ **UserControl1.vb**, ardından **yeniden adlandırmak** kısayol menüsünden. Dosya adını değiştirmek `ValueButton.vb`. Tıklatın **Evet** düğmesini code öğesi 'UserControl1' yapılan tüm başvuruları yeniden adlandırmak istediğiniz sorulduğunda.  
  
4.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.  
  
5.  Açık **ValueButton.vb** Tasarımcısı ile oluşturulan kodun dosyayı görüntülemek için düğümü **ValueButton.Designer.vb**. Bu dosyayı açmak **Kod düzenleyicisinde**.  
  
6.  Bulun `Class` deyimi, `Partial Public Class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>. Bu, tüm işlevselliğini devralmak, devralınan denetimi sağlar <xref:System.Windows.Forms.Button> denetim.  
  
7.  Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satır <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği. Bu özellik yok <xref:System.Windows.Forms.Button> denetim.  
  
8.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
     Görsel Tasarımcı artık kullanılabilir olduğunu unutmayın. Çünkü <xref:System.Windows.Forms.Button> denetim kendi boyama yok, görünümünü Tasarımcısı'nda değiştiremezsiniz. Görsel gösterimi tam olarak bunu devraldığı sınıfı, aynı olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değişiklik sürece.  
  
> [!NOTE]
>  Tasarım yüzeyine hiçbir kullanıcı Arabirimi öğeleri olan bileşenleri eklemeye devam edebilirsiniz.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Devralınan denetiminizi özellik ekleme  
 Bir olası devralınan Windows Forms denetimleri, standart Windows Forms denetimlerine görünümünü ve davranışını (Görünüm) aynıdır, ancak özel özelliklerini ortaya denetimleri oluşturulmasını kullanılır. Bu bölümde, adlı bir özellik ekleyecek `ButtonValue` denetiminiz için.  
  
#### <a name="to-add-the-value-property"></a>Value özelliği eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ValueButton.vb**ve ardından **görünümü kodu** kısayol menüsünden.  
  
2.  Bulun `Public Class ValueButton` deyimi. Hemen bu bildirimi aşağıdaki kodu yazın:  
  
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
  
     Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır. `Get` Deyimi ayarlar özel değişkeninde depolanan değere döndürülen değer `varValue`ve `Set` deyimi kullanarak özel değişkenin değerini ayarlar `Value` anahtar sözcüğü.  
  
3.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-your-control"></a>Denetim test etme  
 Denetimleri tek başına projeleri değildir; bir kapsayıcıda barındırılmalıdır. Denetim test etmek amacıyla çalıştırmak için test projesi için bu sağlamanız gerekir. Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir. Bu bölümde, denetiminizi oluşturabilirsiniz ve bir Windows formunda sınayın.  
  
#### <a name="to-build-your-control"></a>Denetim oluşturmak için  
  
1.  Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.  
  
     Yapı hiçbir derleyici hataları veya uyarılarla başarılı olması gerekir.  
  
#### <a name="to-create-a-test-project"></a>Bir test projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Seçin [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] Projeleri düğümü ve tıklatın **Windows Forms uygulaması**.  
  
3.  İçinde **adı** kutusuna `Test`.  
  
4.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.  
  
5.  İçinde **Çözüm Gezgini**, sağ **başvuruları** , test projeniz için düğümü seçip **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.  
  
6.  Tıklatın **projeleri** sekmesi.  
  
7.  Etiketli sekmesini **projeleri**. `ValueButtonLib` Proje altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
8.  İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Forma denetim ekleme  
  
1.  İçinde **Çözüm Gezgini**, sağ **Form1.vb** ve **Görünüm Tasarımcısı** kısayol menüsünden.  
  
2.  İçinde **araç**, tıklatın **ValueButtonLib bileşenleri**. Çift **ValueButton**.  
  
     A **ValueButton** formda görünür.  
  
3.  Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.  
  
4.  İçinde **özellikleri** penceresinde, bu denetim özelliklerini inceleyin. Bir ek özellik olmasını dışında bunların özdeş standart bir düğme tarafından kullanıma sunulan özellikler için olduğunu unutmayın `ButtonValue`.  
  
5.  Ayarlama `ButtonValue` özelliğine `5`.  
  
6.  Üzerinde **tüm Windows Forms** sekmesinde **araç**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> Formunuza denetim.  
  
7.  Etiket formu merkezine taşımanızı.  
  
8.  Çift `ValueButton1`.  
  
     **Kod düzenleyicisinde** açılır `ValueButton1_Click` olay.  
  
9. Aşağıdaki kod satırını yazın.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. İçinde **Çözüm Gezgini**, sağ **Test**ve seçin **başlangıç projesi olarak ayarla** kısayol menüsünden.  
  
11. Gelen **hata ayıklama** menüsünde, select **hata ayıklamayı Başlat**.  
  
     `Form1`görünür.  
  
12. Tıklatın `Valuebutton1`.  
  
     '5' rakamı görüntülenen `Label1`, gösteren, `ButtonValue` devralınan denetiminizin özelliği için geçirilmiş `Label1` aracılığıyla `ValueButton1_Click` yöntemi. Bu nedenle, `ValueButton` denetimi standart Windows Forms düğme tüm işlevselliğini devralır, ancak ek, özel bir özellik sunar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Bileşen geliştirme izlenecek yollar](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
