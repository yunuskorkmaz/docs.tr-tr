---
title: "İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 668dd3624d06f916b23ec16dd8268d2bae4ffcf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma #
İle [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], güçlü özel denetimlerde oluşturabilirsiniz *devralma*. Devralma sayesinde, tüm standart Windows Forms denetimleri devralınmış işlevselliğini korur, ancak ayrıca özel işlevselliğine sahiptir denetimleri oluşturabilirsiniz. Bu kılavuzda, adlı basit bir devralınan denetim oluşturacak `ValueButton`. Bu düğme standart Windows formlarının dışında işlevselliği devralır <xref:System.Windows.Forms.Button> denetlemek ve adlı özel bir özellik kullanıma `ButtonValue`.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adı ayarlamak için ve varsayılan bileşen doğru ad alanında olduğundan emin olmak için adını belirtin.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib denetim kitaplığı ve ValueButton denetimi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **yeni** ve ardından **proje** açmak için **yeni proje** iletişim kutusu.  
  
2.  Seçin **Windows Forms Denetim Kitaplığı** proje şablonu listesinden [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] projeleri ve türü `ValueButtonLib` içinde **adı** kutusu.  
  
     Proje adı `ValueButtonLib`, kök ad alanı için varsayılan olarak da atanmış. Kök ad derleme bileşenlerinde adlarını nitelemek için kullanılır. Örneğin, iki derleme adlı bileşenleri sağlarsanız `ValueButton`, belirtebilirsiniz, `ValueButton` bileşenini kullanarak `ValueButtonLib.ValueButton`. Daha fazla bilgi için bkz: [ad alanları](../../../csharp/programming-guide/namespaces/index.md).  
  
3.  İçinde **Çözüm Gezgini**, sağ **UserControl1.cs**, ardından **yeniden adlandırmak** kısayol menüsünden. Dosya adını değiştirmek `ValueButton.cs`. Tıklatın **Evet** düğmesini tüm başvurularını kod öğesini yeniden adlandırmak istediğiniz sorulduğunda '`UserControl1`'.  
  
4.  İçinde **Çözüm Gezgini**, sağ **ValueButton.cs** seçip **görünümü kodu**.  
  
5.  Bulun `class` deyimi satır `public partial class ValueButton`, bu denetim devraldığı türünü değiştirip <xref:System.Windows.Forms.UserControl> için <xref:System.Windows.Forms.Button>. Bu, tüm işlevselliğini devralmak, devralınan denetimi sağlar <xref:System.Windows.Forms.Button> denetim.  
  
6.  İçinde **Çözüm Gezgini**, açık **ValueButton.cs** Tasarımcısı ile oluşturulan kodun dosyayı görüntülemek için düğümü **ValueButton.Designer.cs**. Bu dosyayı açmak **Kod düzenleyicisinde**.  
  
7.  Bulun `InitializeComponent` yöntemi ekleme ve kaldırma atar satır <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliği. Bu özellik yok <xref:System.Windows.Forms.Button> denetim.  
  
8.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
    > [!NOTE]
    >  Görsel Tasarımcı artık kullanılamıyor. Çünkü <xref:System.Windows.Forms.Button> denetim kendi boyama yok, görünümünü Tasarımcısı'nda değiştiremezsiniz. Görsel gösterimi tam olarak bunu devraldığı sınıfı, aynı olacaktır (diğer bir deyişle, <xref:System.Windows.Forms.Button>) kodda değişiklik sürece. Tasarım yüzeyine hiçbir kullanıcı Arabirimi öğeleri olan bileşenleri eklemeye devam edebilirsiniz.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Devralınan denetiminizi özellik ekleme  
 Bir olası devralınan Windows Forms denetimleri, Görünüm ve yapısını standart Windows Forms denetimleri aynıdır, ancak özel özelliklerini ortaya denetimleri oluşturulmasını kullanılır. Bu bölümde, adlı bir özellik ekleyecek `ButtonValue` denetiminiz için.  
  
#### <a name="to-add-the-value-property"></a>Value özelliği eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **ValueButton.cs**ve ardından **görünümü kodu** kısayol menüsünden.  
  
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
  
     Bu kod yöntemleri olarak ayarlar `ButtonValue` özelliği depolanır ve alınır. `get` Deyimi ayarlar özel değişkeninde depolanan değere döndürülen değer `varValue`ve `set` deyimi kullanarak özel değişkenin değerini ayarlar `value` anahtar sözcüğü.  
  
3.  Gelen **dosya** menüsünde seçin **Tümünü Kaydet** projeyi kaydetmek için.  
  
## <a name="testing-your-control"></a>Denetim test etme  
 Denetimleri tek başına projeleri değildir; bir kapsayıcıda barındırılmalıdır. Denetim test etmek amacıyla çalıştırmak için test projesi için bu sağlamanız gerekir. Ayrıca, Denetim test projesi için erişilebilir (derleme) oluşturarak yapmanız gerekir. Bu bölümde, denetiminizi oluşturabilirsiniz ve bir Windows formunda sınayın.  
  
#### <a name="to-build-your-control"></a>Denetim oluşturmak için  
  
1.  Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.  
  
     Yapı hiçbir derleyici hataları veya uyarılarla başarılı olması gerekir.  
  
#### <a name="to-create-a-test-project"></a>Bir test projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsündeki **Ekle** ve ardından **yeni proje** açmak için **Yeni Proje Ekle** iletişim kutusu.  
  
2.  Seçin **Windows** düğümü, beneath **Visual C#** düğümü ve tıklatın **Windows Forms uygulaması**.  
  
3.  İçinde **adı** kutusuna `Test`.  
  
4.  İçinde **Çözüm Gezgini**, sağ **başvuruları** , test projeniz için düğümü seçip **Başvuru Ekle** görüntülemek için kısayol menüsünden  **Başvuru ekleme** iletişim kutusu.  
  
5.  Etiketli sekmesini **projeleri**. `ValueButtonLib` Proje altında listelenir **proje adı**. Projeyi test projesinin başvuru eklemek için çift tıklayın.  
  
6.  İçinde **Çözüm Gezgini** sağ **Test** seçip **yapı**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Forma denetim ekleme  
  
1.  İçinde **Çözüm Gezgini**, sağ **Form1.cs** ve **Görünüm Tasarımcısı** kısayol menüsünden.  
  
2.  İçinde **araç**, tıklatın **ValueButtonLib bileşenleri**. Çift **ValueButton**.  
  
     A **ValueButton** formda görünür.  
  
3.  Sağ **ValueButton** seçip **özellikleri** kısayol menüsünden.  
  
4.  İçinde **özellikleri** penceresinde, bu denetim özelliklerini inceleyin. Bir ek özellik olmasını dışında bunların özdeş standart bir düğme tarafından kullanıma sunulan özellikler için olduğunu unutmayın `ButtonValue`.  
  
5.  Ayarlama `ButtonValue` özelliğine `5`.  
  
6.  İçinde **tüm Windows Forms** sekmesinde **araç kutusu**, çift **etiket** eklemek için bir <xref:System.Windows.Forms.Label> Formunuza denetim.  
  
7.  Etiket formu merkezine taşımanızı.  
  
8.  Çift `valueButton1`.  
  
     **Kod düzenleyicisinde** açılır `valueButton1_Click` olay.  
  
9. Aşağıdaki kod satırını ekleyin.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. İçinde **Çözüm Gezgini**, sağ **Test**ve seçin **başlangıç projesi olarak ayarla** kısayol menüsünden.  
  
11. Gelen **hata ayıklama** menüsünde, select **hata ayıklamayı Başlat**.  
  
     `Form1`görünür.  
  
12. Tıklatın `valueButton1`.  
  
     '5' rakamı görüntülenen `label1`, gösteren, `ButtonValue` devralınan denetiminizin özelliği için geçirilmiş `label1` aracılığıyla `valueButton1_Click` yöntemi. Bu nedenle, `ValueButton` denetimi standart Windows Forms düğme tüm işlevselliğini devralır, ancak ek, özel bir özellik sunar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bileşenleri ile programlama](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Bileşen geliştirme izlenecek yollar](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Nasıl yapılır: bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [İzlenecek yol: Visual C# ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
